---
title: "Steam won't launch (You are missing the following 32-bit libraries)"
date: 2015-01-18
forum: Gaming &amp; Leisure
---

### Post by josh109 on 2015-01-18
I for some reason can't open Steam. It worked for a while before but  it suddenly stopped working. Here's the error that shows up:


  You are missing the following 32-bit libraries, and Steam may not run:
libbz2.so.1.0

---

### Post by oldrocker99 on 2015-01-18
Try this:
```
sudo apt-get install libbz2-1.0:i386
```
This **should** work; all 32-bit libraries for a 64-bit system end in :i386, so you know.

Don't be afraid to ask questions here. That is what these forums are **for!**

---

### Post by josh109 on 2015-01-18
> **oldrocker99 said:**
> Try this:
```
sudo apt-get install libbz2-1.0:i386
```
This **should** work; all 32-bit libraries for a 64-bit system end in :i386, so you know.

Don't be afraid to ask questions here. That is what these forums are **for!**

Did this. Seemed to fix it. Kinda.

I don't get the error when I start Steam, but Steam doesn't start.

When running from "steam" from terminal I get the following output:


joshua@LITECOINRIG:~$ steam
Running Steam on ubuntu 14.10 64-bit
STEAM_RUNTIME is enabled automatically
joshua@LITECOINRIG:~$

---

### Post by efflandt on 2015-01-19
What video card/chip do you have and video drivers? Did you install steam from Software Center or the deb file from store.steampowered.com website? It is possible that your steam needs to update, but usually it does that automatically then restarts. Make sure that a broken steam is not still running in the background, because only one instance will run at a time. There also was an issue if you ran steam as one user and then tried to run it has another Linux user it would leave something in /tmp that only had permissions for first user. I don't know if that has been fixed in regular steam client or if you enable Steam Beta once you get a client started. Have you rebooted since you first tried to run steam just to make sure any other instance or /tmp file was cleared?

I just fresh installed 64-bit 14.04.1 within past 2 weeks, installed Steam from Software Center, but copied my home directory over from 12.04 which had my game files, etc. I did not need to install any other i386 libs. The steam beta client has gone through some updates since then. You should normally see something like this when you launch steam from a terminal, up to the point that it brings up the steam login gui:```
efflandt@XPS-8100-1404:~$ steam
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1421464441)
Installing breakpad exception handler for appid(steam)/version(1421464441)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steamwebhelper)/version(20150116184127)
Installing breakpad exception handler for appid(steamwebhelper)/version(1421433687)
[0119/073242:ERROR:nss_util.cc(1018)] Failed to load NSS libraries.
Installing breakpad exception handler for appid(steamwebhelper)/version(20150116184127)
Installing breakpad exception handler for appid(steamwebhelper)/version(1421433687)
Installing breakpad exception handler for appid(steamwebhelper)/version(1421433687)
Installing breakpad exception handler for appid(steam)/version(1421464441)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1421464441)
Installing breakpad exception handler for appid(steam)/version(1421464441)
Installing breakpad exception handler for appid(steam)/version(1421464441)
Installing breakpad exception handler for appid(steam)/version(1421464441)
Installing breakpad exception handler for appid(steam)/version(1421464441)
FillInMachineIDInfo took a total of 0 milliseconds
Installing breakpad exception handler for appid(steam)/version(1421464441)
Installing breakpad exception handler for appid(steam)/version(1421464441)
Installing breakpad exception handler for appid(steam)/version(1421464441)
Generating new string page texture 7: 128x256, total string texture memory is 131.07 KB
Generating new string page texture 8: 48x256, total string texture memory is 180.22 KB
Generating new string page texture 9: 256x256, total string texture memory is 442.37 KB
Generating new string page texture 10: 64x256, total string texture memory is 507.90 KB
```

---

