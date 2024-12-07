This repository contains patches for [typelevel/doobie](https://github.com/typelevel/doobie )

# `pos-line-0` branch

Modified not to auto-generate the line number, always setting it to be 0.

1. Background
    1. Doobie macro generates `Pos` object to hold the source position of the sql strings, for diagnostics purpose.

1. Use cases
    1. A crude way to check if a refactoring changes the logic is to compare the compiled class files.
        1. Even with compile flag `-g:none` that strips the debug information,
           the class file might still change because of the generated `Pos`.
            1. This branch avoids that.

1. How to use
    1. Cross build with sbt

           + free/packageBin

    1. Copy a jar file in `modules/free/target` to `unmanagedBase` (`lib` directory) of the target project.
