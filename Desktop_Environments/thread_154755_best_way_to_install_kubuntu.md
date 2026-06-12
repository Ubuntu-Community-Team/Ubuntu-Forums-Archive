---
title: "best way to install kubuntu?"
date: 2006-04-03
forum: Desktop Environments
---

### Post by crazedcougar on 2006-04-03
Hi,

I'm using an amd64 system and am considering switching from 32bit gentoo w/ kde to 32 or 64 bit kubuntu with kde.  What is the best way to achive kde goodness, why?  The two options i have heard of are download kubuntu dvd/cd or download ubuntu dvd/cd and then apt-get kde.  Is there a common prefrence?

Thanks!

---

### Post by bluevoodoo1 on 2006-04-03
After installing GNOME, I've used... 

sudo apt-get install kubuntu-desktop

without any problems (to have GNOME and KDE on my system.)

---

### Post by eriefisher on 2006-04-03
If you want KDE and you going to download one anyway, I would just download Kubuntu. You can always get the Ubuntu-desktop packages later if you want. That's just my 2 cents.

eriefisher

---

### Post by Burgresso on 2006-04-03
If you are noobish (not quite a noob, but still not very skilled in linux) I'd download or get Ubuntu and get it working - like the internet connection and everything - then install Kubuntu. When I tried to install Kubuntu off the disk it didn't work very well, but it was probally user error. ;)

---

### Post by crazedcougar on 2006-04-03
I've been running gentoo for a while, i consider myself at least kinda competent :)  Will kubuntu actually differ from ubuntu, besides that kde is pre-installed?  What about arts and alsa?

---

### Post by Parkotron on 2006-04-05
I you plan to use KDE, download Kubuntu. Since you're coming from Gentoo, I would guess you like things fast and light. If you install Ubuntu and then add KDE you'll still have a full Gnome install on your system, which if you never plan to use Gnome, seems like a waste both of bandwidth and diskspace.

Ubuntu, Kubuntu, Edubuntu, Xubuntu are all the same distrubution, sharing the same repositories. They differ only in what is installed be default. The only area where Ubuntu really seems to be leading Kubuntu at the moment is in network configuration, especially wireless. But if you consider yourself a competent Linux user, you'll probably not have too much trouble.

As far as Arts and ALSA, I've never had an issue here. *buntus all use ALSA and Arts seems to get along well with it.

---

### Post by crazedcougar on 2006-04-05
"*buntus," i like it :D  Thanks for the info, kubuntu it is!  Now just to decide 32 or 64 bits... (see my other thread [here](http://ubuntuforums.org/showthread.php?t=154756))

---

### Post by aysiu on 2006-04-05
[QUOTE=bluevoodoo1]After installing GNOME, I've used... 

sudo apt-get install kubuntu-desktop

without any problems (to have GNOME and KDE on my system.)[/QUOTE] It's probably best to do ```
sudo aptitude install kubuntu-desktop
``` as it makes Kubuntu easier to remove should you later desire to do so.

---

### Post by jetpeach on 2006-04-07
curious, why does using aptitude instead of apt-get help make it easier to install?

I run kubuntu that was originally a gnome ubuntu install and don't have many problems now.  At first, there were a few issues, things like sound in flash, which gnome and kde defaulted to different sounds settings or something.  I got them all worked out without too much trouble though and have been running kde smooth lately, now having gone to dapper (i couldn't restist amarok 1.4beta, but to run it I needed the dapper packages...).

Anyway, if you've been running gentoo I'm sure you know all this :)

---

### Post by aysiu on 2006-04-07
[QUOTE=jetpeach]curious, why does using aptitude instead of apt-get help make it easier to install?[/QUOTE] It doesn't. Installing with aptitude makes it easier to **un**install later (if you decide you don't like it and don't want it taking up space).

---

### Post by senorian on 2006-04-10
Re: aptitude
I did a search but could not find a review or any general info.
Is there any review of "automatix"."Klik", "easyubuntu","autopackage","zeroinstall",Oblisk" (and any others?)
Especially with respect to the ease(and completeness) of uninstalling?
Thanks
(edit)
Just saw the following
Canonical Ltd. - Is funding Smart development since September of 2005.
([http://labix.org/smart](http://labix.org/smart))
So is there more info about "smart"?

---

