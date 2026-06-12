---
title: "First time Kubuntu user, A few different problems, Kwallet &amp; Online Accounts"
date: 2017-07-13
forum: Desktop Environments
---

### Post by overlord-daemon on 2017-07-13
Kubuntu is looking pretty good.  I was getting spammed with a constantly popping up dialog box asking for some kind of password.  I tried entering my password to no avail.  I figured out after much frustration that it was something called Kwallet.  I turned it off in settings and that did the trick.  I am concerned about the issues I may face in turning it off.  Is it safe to do so.  I also deleted the wallet.  I tried to make a new wallet and it says no keys found or something like that.  Since I have disabled the Kwallet pop-up I have had no problems.  What little research I could find on the Internet says I do not need to worry since I use Firefox because Firefox uses it's own secure password system.  I have no need to worry also as this is a desktop in my house and I was smart enough to select the encrypted home folder option during install.

The only question that remains is there something that Kwallet provides that might make it worthwhile to turn it back on.  But and this is a big but, If I have to enter my password twice then I don't want to turn Kwallet on.  I want everything unlocked when I log on.  My research into the terminal and the software update mechanism have convinced me those are really the only two items that I will accept as having to enter a password.  I can see why they need to be password protected with sudo and why software update must be password protected.  But everything else has to be unlocked including annoying pop-up Kwallet.

_***My second problem***_ is in System Settings/On-line account.  When trying to setup an Google account a dialog box pops up with an error.  I have included a screen-shot.
[ATTACH=CONFIG]275986[/ATTACH]

Everything else is splendid.  I have resurrected a 2003 Dell Dimension 4550 desktop with 1GB ram and 500GB hard drive.  Everything is perfect.  I even added in a 4 port USB 2.0 PCI card and a 100MBps add in networking card and an AMD AGP card that does 3D.  All connected to a DVI digital 22 inch wide screen 1680x1050 monitor.  Thank you thank you.  We love out new desktop.  We do have to be careful not to open more than two tab in Firefox and we must be patient.  We thought that maybe a lightweight OS like Lubuntu might work, but then we thought that we are happy to have a slightly slow desktop that is way more than usable.  We don't want to give the impression that it's real slow.  It is very fast considering it is modern OS on old hardware.

We love Kubuntu.  I also added in a blue-tooth adapter.  Now our 2003 computer can do so many things that Dell did not think of in 2003.  I will try to add this cool file called lshw.  It is my first sudo file.  It was how I found the the desktop would work.  All I had to do was look for red.  The Internet say that the smsbus is no problem.

---

### Post by vasa1 on 2017-07-13
> **overlord-daemon said:**
> ...
The only question that remains is there something that Kwallet provides that might make it worthwhile to turn it back on.  But and this is a big but, If I have to enter my password twice then I don't want to turn Kwallet on.  I want everything unlocked when I log on.  My research ...
See if [https://wiki.archlinux.org/index.php/KDE_Wallet#Unlock_KDE_Wallet_automatically_on_login](https://wiki.archlinux.org/index.php/KDE_Wallet#Unlock_KDE_Wallet_automatically_on_login) fulfils your "I want everything unlocked when I log on" condition.

IMPORTANT: Please mention the version of your distro in your post. People may not be inclined to download an unsolicited compressed file. And the advice most certainly will be dependent on the version of your OS (and whether it's fully updated).

Please post the output of```
lsb_release -a
``````
uname -a
```and```
apt policy kwin plasma-desktop | grep -i installed
```

---

