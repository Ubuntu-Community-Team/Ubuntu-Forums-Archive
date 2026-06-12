---
title: "kubuntu 8.10 downgrading bluez?"
date: 2009-01-01
forum: Desktop Environments
---

### Post by daryl314 on 2009-01-01
hi all,

i'm trying to get bluetooth to work in kubuntu 8.10.  the bug report suggests
"For those who just want to use bluetooth under KDE: 1. downgrade your bluez packages and install the latest available bluez-libs-3.x and bluez-utils-3.x (should be 3.36) 2. use kbluetooth4 under KDE4 or kbluetooth under KDE3"
[https://bugs.kde.org/show_bug.cgi?id=172267#c8](https://bugs.kde.org/show_bug.cgi?id=172267#c8)

unfortunately i have no idea how to do this.  could anyone point me in the right direction?  i am also willing to use command-line approaches to get bluetooth working.

```
sudo hidd --search
``` works to connect my mouse if i have in pairing mode, but the connection fizzes out if my laptop suspends, or if i reboot the machine.

i read through the forums, and it sounds like a lot of people are having problems.  unfortunately none of the suggestions have worked for me.

thanks,
daryl

---

### Post by emuman on 2009-01-07
I recompiled bluez 3.36 and kbluetooth4, but pairing didn't worked for me. Are there any precompiled bluez 3.36 packages for kubuntu 8.10? Is there a timeline for porting kbluetooth to bluez 4?

---

### Post by awry on 2009-01-14
I think it's more complicated than just recompiling bluez3 and kdebluetooth4.  Bluez support is integrated into solid, which is part of KDE.  Solid is in one (or more) of the kdebase packages, I believe, but I'm not sure which one(s).  So first you need to rebuild bluez3, probably need to rebuild libbluetooth2 and libbluetooth2-dev (possibly even before bluez3), then rebuild the relevant kdebase packages (to link solid against your newly built bluetooth libs), then finally recompile kdebluetooth4.

To complicate things even more, many package names changed with the appearance of bluez4, so some of the package dependencies need to be manually tweaked and/or forced.  

Overall, it's going to take a good bit of effort, and I'm wondering if there's a distritubion out there with kde-4.2 and working bluetooth for me to switch to (but not rpm based).

I've tried install gnome-bluetooth and bluez-gnome as substitutes, but so far haven't had good luck with them.  Bluetooth seems pretty borked in intrepid overall, and it's pretty disappointing.

---

