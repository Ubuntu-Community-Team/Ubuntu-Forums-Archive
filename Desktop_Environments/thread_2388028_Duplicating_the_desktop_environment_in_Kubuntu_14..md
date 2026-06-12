---
title: "Duplicating the desktop environment in Kubuntu 14.04"
date: 2018-03-27
forum: Desktop Environments
---

### Post by pwabrahams on 2018-03-27
I'm moving to a new laptop, and I want to duplicate current desktop environment on the new machine.  I particularly want to duplicate the multiple desktops and their wallpapers  I tried copying my old home directory wholesale, but that didn't work; too many errors because of the different architecture.   I think that copying the appropriate dotfiles will do the trick, but I don't know where within the dotfiles the necessary information lives.  Just what should I be copying?  Or perhaps an easier question: where can I find documentation on **.local** and such?

---

### Post by TheFu on 2018-03-27
**aptik** is probably what you want. I've never used it.

But system settings are in /etc/ and personal settings are in your HOME- also called ~/.

I just backup my HOME and restore it to the new machine.  Then use a list of manually installed packages (apt-mark) to shovel in that list of manually installed packages on the new machine.  This is usually sufficient for typical desktop users.  If you run apache, nginx, mariaDB or postgres or postfix, then there are files elsewhere that you already know to get.

Different architecture hasn't mattered for settings on my systems, but I haven't used KDE in a very long time. I have moved from 32--->64 bit systems and moved settings for Firefox and Thunderbird across Windows, OSX and Linux successfully.  All were x86-like systems.  I haven't tried to move them to/from ARM or Power or SPARC or MIPS based-systems.

[https://askubuntu.com/questions/167955/taking-kde-config-files-with-me](https://askubuntu.com/questions/167955/taking-kde-config-files-with-me) says that different KDE releases use different locations and different toolkits different still.  An interesting solution to compatibility issues.

---

### Post by springshades on 2018-03-28
Have you tried copying the  ~/.local/share/plasma folder to the new system? This shouldn't be as bad as copying your entire home folder. The other folder that could be important is  ~/.kde/share. There are a bunch of other settings in ~/.local/share, but they are mostly settings for individual KDE apps. That's more likely to cause errors since there is no guarantee that your apps will be the exact same versions.

I could be wrong, but my guess is that this will not copy over some of the themes and artwork that you've downloaded which may be necessary to duplicate your desktop.

---

### Post by speartip on 2018-03-28
Just a thing. Didn't Kubuntu 14.04 reach end of life in April 2017?

---

### Post by oldos2er on 2018-03-28
According to [https://kubuntu.org/news/kubuntu-14-04-lts/](https://kubuntu.org/news/kubuntu-14-04-lts/) it's supported until 2019.

---

### Post by speartip on 2018-03-29
> **oldos2er said:**
> According to [https://kubuntu.org/news/kubuntu-14-04-lts/](https://kubuntu.org/news/kubuntu-14-04-lts/) it's supported until 2019.
Apologies. I thought 12.04 was the last 5 year supported Kubuntu.

---

