# postmarketos-samsung-a05s

postmarketOS for Samsung Galaxy A05s

## Current status

The kernel successfully compiles, but it panics on boot, meaning postmarketOS cannot boot on this phone (yet).

## How to install/experiment

Use [pmbootstrap](https://wiki.postmarketos.org/wiki/Pmbootstrap) on a Linux system. Before proceeding, flash [TWRP](https://github.com/SavedByLight/Custom-Recovery-Builder/releases/download/03%2F01%2F2025-a05s-002/recovery.img) onto your phone, enable USB debugging on the phone, and install Android platform tools (adb and fastboot) on the Linux system.

- After installing pmbootstrap, run `pmbootstrap init` to initialize its work folders. Choose "samsung" as the vendor, "a51" as the codename, and "xfce4" as the user interface. Take note of the folder pmbootstrap clones pmaports.git into.
  - We're choosing the Galaxy A51 as the device in this stage as we need to copy the Galaxy A05s aports after we finish initializing our pmbootstrap environment.
- Copy the Galaxy A05s aports (`device-samsung-a05s` and `linux-samsung-a05s`) into `<pmaports.git folder>/device/testing`.
- Re-run `pmbootstrap init`, this time picking "a05s" as the codename.
- Build the Galaxy A05s aports (this will take a long time):
```
$ pmbootstrap build linux-samsung-a05s
$ pmbootstrap build device-samsung-a05s
```
- Prepare the postmarketOS rootfs by running `pmbootstrap install`.
- Connect your phone into the Linux system, then reboot your phone into fastboot mode using ADB (`adb reboot fastboot`) on your Linux system.
- Flash postmarketOS onto the device by running the flasher commands printed at the end of `pmbootstrap install`.
- Reboot your phone to the installed system.
- Profit! (more like Loss lol)

## Credits

- [@cd-Crypton](https://github.com/cd-Crypton) - [kernel source code](https://github.com/cd-Crypton/android_kernel_samsung_bengal-5.15/tree/android-13)
