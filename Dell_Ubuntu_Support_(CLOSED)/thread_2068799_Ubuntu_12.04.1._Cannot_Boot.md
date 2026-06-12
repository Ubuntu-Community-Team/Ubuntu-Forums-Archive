---
title: "Ubuntu 12.04.1. Cannot Boot"
date: 2012-10-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by winstonebook on 2012-10-09
I was installing Wubi, and I was chatting on the Ubuntu IRC Network about my sound driver problem. When Wubi was finished installing I restarted my computer and it went into Ubuntu without any boot menu. I did a hard shutdown and restarted my computer, and the boot menu was there so I chose Ubuntu. It says "Ubuntu is preparing to run Ubuntu for the first time" or something like that. Then there was a black screen and it stayed there for a long time so I did a hard shutdown again. When I turned it back on and selected Ubuntu from the list it still said the same thing, but after it loaded a thing called BusyBox, which was this little command prompt. Restarted, nothing had changed. So I booted into Windows (Windows 7) and hit F8 on my computer and chose Repair my Computer and opened the command prompt and ran chkdsk /r (its still running, lets see if it does any good). I need help.

---

### Post by gerrman97 on 2012-10-22
what version of windows 7 do you have? i might be able to help

---

### Post by Karlchen on 2012-10-22
Hello, winstonebook.

You know that any Wubi installation consists of two phases?
The first phase is run by wubi.exe inside Windows. It prepares the second phase which is the real Linux installation. The Linux installation is done by Linux itself. (Wubi has prepared the required live and installation system on your harddisk.)

The only time that Wubi reboots the machine directly into Linux without giving you the choice of selecting something else is when it has finished its job under Windows and when it reboots into the Linux live system - now on your harddisk - in order to automatically start the regular Linux installation.

If this reboot is the reboot which you interrupted by powering off the machine, then congratulation. The real Linux installation has never been performed.

I suggest to launch Windows, uninstall Wubi and start all over again. Maybe you should simply follow the [Wubi Guide - Installation]("https://wiki.ubuntu.com/WubiGuide#Installation") and refrain from performing hard shutdowns. They are only required if a system has got completely stuck and does not even respond to <ctrl><alt><del>. I would not recommend interrupting the Linux installation process by pressing <ctrl><alt><del>, either, unless you absolutely have to, because the process has got stuck.

HTH,
Karl

---

