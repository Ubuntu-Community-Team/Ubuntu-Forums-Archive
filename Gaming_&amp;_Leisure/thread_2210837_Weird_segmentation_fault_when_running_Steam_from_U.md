---
title: "Weird segmentation fault when running Steam from Ubuntu's Software Centre"
date: 2014-03-12
forum: Gaming &amp; Leisure
---

### Post by silex89 on 2014-03-12
Hi there guys. Long time no see and here I'm today, starting a new chapter with Ubuntu :)!. Glad to be back!

Here's the deal: I installed Ubuntu 13.10 on my new Sony VAIO Laptop on UEFI mode (no Win 8.1, just Ubuntu as the only OS). Everything works ok. I've downloaded the Steam bootstraper from the Ubuntu Software Centre but I can't go past the License window. As soon as I hit the "I agree" button the client crashes and the download of the Steam Client doesn't start.

So, I deleted all the files and folders from my home directory that were related to Steam, uninstalled the bootstraper and tried with the version that is in the official web page. I had the exact same issue. I tried to run bootstraper from a terminal and I got this output (from both installers)

```
daniel@Ophiel:~$ steam
Setting up Steam content in /home/daniel/.local/share/Steam
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Couldn't dlopen libudev.so.1 or libudev.so.0, driver detection may be broken.
steam: ../../../../src/loader/loader.c:129: asserted_dlsym: La declaración `result' no se cumple.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2014-03-12 23:22:14] Startup - updater built Aug  1 2013 13:35:53
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140312232214_1.dmp
/home/daniel/.local/share/Steam/steam.sh: línea 704:  4668 Aborted                (`core' generated) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Installing bootstrap /home/daniel/.local/share/Steam/bootstrap.tar.xz
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME has been set by the user to: /home/daniel/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Couldn't dlopen libudev.so.1 or libudev.so.0, driver detection may be broken.
steam: ../../../../src/loader/loader.c:129: asserted_dlsym: La declaración `result' no se cumple.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2014-03-12 23:22:17] Startup - updater built Aug  1 2013 13:35:53
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-765525ab-d93f-4676-a573-32ee22140312
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140312232217_1.dmp
/home/daniel/.local/share/Steam/steam.sh: línea 704:  4780 Aborted                (`core' generated) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-8a08c10b-47b1-456e-bd96-318792140312

```

I have little idea when it comes to read something like this. But in my experience when there's a "core generated" kind of output, it's referable to a segmentation fault.

The packages I'm currently using on my system are Unity's default configuration, oibaf's PPA to get the latest open source drivers for my ATI Richland APU and the Trusty Tahr's kernel (version 3.13.1 which I installed manually using [these packages]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.1-trusty/")). I was running Arch Linux with Steam and with the open source drivers and the newest kernel was more than enough to play the games that I own, that's why I don't really want to switch to Catalyst.

Do you guys have an idea?

Thanks in advance.

Cheers!

---

