---
title: "Unity and Gnome not working properly"
date: 2011-06-28
forum: Desktop Environments
---

### Post by EVILCOOKIE on 2011-06-28
Hello, everyone, natty user here. I'm having trouble with Unity and Gnome (with effects); for starters, there's a huge black rectangle on both environments, anything I open is not shown on the screen and there's lots of graphical glitches. I can only boot into Ubuntu using Gnome without effects (Ubuntu Classic (no effects)).

I'm not very experienced with Ubuntu yet (I've been using it for 3 months only)

Also it is worth mentioning that I reinstalled Ubuntu 3 times already and this happened after I updated, installed Compiz and xorg ati drivers and rebooted. I don't have much of a problem using Gnome, but I'd like to fix this because i'm used to Unity.

My specs are:
ATI Radeon X300
AMD Athlon 3800+ @ 2.4 Ghz
1 GB RAM

Below are 2 screencaps of what is shown on my screen after I log in. Left is Gnome and right is Unity.
I could also reinstall Ubuntu once more, but I don't know what's causing the problem and it will probably happen again.
Any help will be appreciated.

---

### Post by Alwimo on 2011-06-28
You could check additional drivers (under the System > Administration menu in GNOME 2 or by searching for "additional drivers" in Unity) and see if there are proprietary drivers available for your graphics card.

Install them, or if it is installed, try uninstalling it.

---

### Post by EVILCOOKIE on 2011-06-28
I've downloaded the proprietary ATI driver from the repositores, but when I click System->Administration->Additional Drivers nothing appears. It says searching for drivers and then an empty window shows up. Do I need to purge the x.org drivers first?

When I input fglrxinfo at the terminal It responds with "Segmentation fault".

---

### Post by Krytarik on 2011-06-29
Your video card isn't supported by the proprietary driver anymore. If you installed it, this may be the cause of your issues. See this guide on how to remove it and reinstall the default driver:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

If you still have issues thereafter, you may try upgrading the video driver through Xorg-Edgers' PPA, it offers more recent drivers than the offical repos. Notice that this would upgrade a lot of other packages as well.

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```If you need/want to remove those PPA and downgrade the concerning packages again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```Greetings.

---

### Post by EVILCOOKIE on 2011-06-29
Thanks for the help.
I already removed the fglrx package, but I never got it working because, as I mentioned previously, nothing appeared on the additional drivers window. Anyway, I purged both fglrx and radeon driver, then reinstalled the latter, but to no avail.

I already added the xorg-edgers ppa and reinstalled the radeon driver, but it's still the same. I'm considering formatting again, but I don't know how to prevent this from happening because as soon as I update (note: hundreds of packages) and reboot the screen screws up again.

---

### Post by EVILCOOKIE on 2011-07-05
Bump. Sorry, but no one answered and I still have my problem...
I installed Unity 2D and it's quite good provisionally, but i still can't log in on Unity 3D or Gnome. Any help?

EDIT: I solved my issue by reinstalling Ubuntu, please close this thread.

---

