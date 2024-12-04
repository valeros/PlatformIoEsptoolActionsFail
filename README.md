# PlatformIO `esptool` fail on `merge_bin` operation in Github Actions

This repo demonstrates an issue with the invocation of `merge_bin` command using `platformio/tool-esptoolpy` as a pio tool when running in Github Actions runner. A `UserSideException: [Errno 13] Permission denied: 'esptool'` is produced. The error appears on both Windows and Ubuntu.

Extract of the logs from the failed Github Actions run on Ubuntu (check the [Actions tab](/actions) for the full logs):

> `Run pio pkg exec --package "platformio/tool-esptoolpy" -- esptool --chip esp32 merge_bin --output output.bin 0x1000 test1.bin 0x2000 test2.bin`
>
> `Tool Manager: Installing platformio/tool-esptoolpy`
>
> `Downloading 0% 10% 20% 30% 40% 50% 60% 70% 80% 90% 100%`
>
> `Unpacking 0% 10% 20% 30% 40% 50% 60% 70% 80% 90% 100%`
>
> `Tool Manager: tool-esptoolpy@1.40501.0 has been installed!`
>
> `Using tool-esptoolpy@1.40501.0 package`
>
> `UserSideException: [Errno 13] Permission denied: 'esptool'`
>
> `Error: Process completed with exit code 1.`

Calling the same command `merge_bin` through `python -m esptool` works.
