---
title: "Sidux 2007-03 Is Now Available for Both Amd64 and i686"
date: 2007-08-16
forum: Debian
---

### Post by Dark Star on 2007-08-16
[IMG]http://www.imgx.org/pfiles/1444/sidux-logo.png[/IMG] Based on the Debian Sid distribution, Sidux also comes with its own packages and scripts and contains only dfsg free software. However this doesn’t mean you cannot add some non-free ones. Fell free to add as many sources as you want to the /etc/apt/sources.list.
 [CENTER][[IMG]http://forums.erodov.com/imagehosting/thum_59464fa482dd0aa.gif[/IMG]]("http://forums.erodov.com/vbimghost.php?do=displayimg&imgid=376")[/CENTER]
 [I][B]
Highlights:[/B][/I]
 [LIST]
[*] amd64 (AMD64, Intel Core2, newer 64 bit capable AMD Sempron and Intel Pentium 4 and i686 (Pentium pro/ Pentium II, AMD K7 Athlon or newer).
[*] kernel 2.6.22.3-rc1 (smp, hard preemption)
[*] minimal, but fully functional KDE 3.5.7 (English + Deustch)
[*] completely overhauled init sequence
[*] completely refactored installer backend
[*] new artwork created by cleary and the sidux art team
[*] offline manual for en + de (. only available on the running live CD or the installed system.), online manuals for more languages online at [sidux manual]("http://manual.sidux.com/") and available via apt
[*] lots of changes in the manua
[*] rt2×00 2.0.6+git20060810 support for RaLink cards supporting wpsupplicant, remove /etc/modprobe.d/mac80211 to prefer it over RaLink legacy drivers
[*] support for RealTek RTL8187 wlan cards
[*] libata support for parallel ATA systems
[*] enhance hardware support libraries
[*] support for “smxi”, replacing “sm” and “du-fixes-h2.sh”
[*] bugfix for keyboard layout selections in X
[*] USB scanner support has been fixed in kernel ( &#8805;2.6.22.1-slh-smp-7/ &#8805;2.6.22.1-slh64-smp-7)
[*] fix XDG menu entry for My-PPPoE Conf
[*] add siduxcc and kooka.
[*] thanks to concerted team efforts, the dependencies on Xdialog and threfore gtk+ 1.2 could be removed
[*] support for Agere Systems et131x ethernet controllers
[*] fw-detect to probe for hardware with non-free needs
[*] rt73-legacy driver
[*] memtest86+
[*] added iputils-ping
[*] added VDR 1.4.7
[*] partition detection bug fixed[/LIST] [CENTER][[IMG]http://forums.erodov.com/imagehosting/thum_59464fa46e9609a.gif[/IMG]]("http://forums.erodov.com/vbimghost.php?do=displayimg&imgid=375")[/CENTER]
 Home Page : [SIdux]("http://www.sidux.org/")
 Announcment :  [Official Site]("http://sidux.com/Article286.html")

---

### Post by angryfirelord on 2007-08-16
I still don't understand why the Sidux devs insist on using apt-get over aptitude. I update y Lenny system with aptitude and nothing has ever broken.

Anyway, if you want a nice, fast paced distro, Sidux is definitely one to try (although one can get a similar system by pointing Debian's sources to unstable).

---

