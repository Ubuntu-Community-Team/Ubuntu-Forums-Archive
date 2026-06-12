---
title: "KDE Icons/Style Showing Up in Unity?"
date: 2015-11-14
forum: Desktop Environments
---

### Post by jonathan90 on 2015-11-14
I installed KDE yesterday, and for some reason the KDE style/icons are showing up in Unity.  I see this in the default fonts, the scroll bars, the wifi selection, autofill, and so on.  Is there anyway to fix this, or do I need to get rid of KDE entirely.  Also, Ubuntu boots with the "Kubuntu" screen and GRUB is black instead of purple.

---

### Post by grahammechanical on 2015-11-14
Yes, what you are seeing is the normal behaviour of an alternative desktop. Different desktop environments use the same configuration scripts. So, installing an alternative desktop environment will overwrite some existing configuration scripts. And short of a fresh install it is no easy task rearranging things.

Regards.

---

### Post by jonathan90 on 2015-11-14
But if I remove KDE, will it return to normal?

---

### Post by jonathan90 on 2015-11-15
And if so, how should I remove it without damaging my system?

---

### Post by Bucky Ball on 2015-11-16
No idea how to remove KDE DE. How did you install it? That should get you back to somewhere close to what it was, then you could reinstall Unity desktop environment, which might fill in any gaps that KDE drags out with it, and see how you go.

---

### Post by jonathan90 on 2015-11-16
I installed it using 
```
sudo apt-get install kubuntu-desktop
```

 and I tried using 

```
sudo apt-get remove kubuntu-desktop
```

but it didn't remove anything.

---

### Post by Bucky Ball on 2015-11-16
That's not installing kde. That is installing Kubuntu and all its default apps along with what you already had there. *buntu-desktop anything doesn't install only the desktop environment and it is a common misconception we see around here regularly (as is your situation consequently) that it does.

As an example, xubuntu uses the xfce4 desktop environment. If you want to try the desktop environment you install xfce4.

```
sudo apt-get install xfce4
```

Installing 'xubuntu-desktop' effectively installs Xubuntu. If you started with a minimal install, which has no apps and no DE, and you installed xubuntu-desktop, the end result would be an Xubuntu install. 

You don't install the Xubuntu desktop. That is totally different. Kubuntu uses KDE. What would you install? KDE. kubuntu-desktop achieves a totally different outcome. Sure, you'll get the KDE desktop environment, but you'll also get everything else from KDE, as you have discovered. 

If the command you tried did nothing I'm not sure where you go from here. :(

---

### Post by jonathan90 on 2015-11-16
But is there anyway to get Kubuntu to stop interfering with the style in Unity? If it weren't for the weird fonts and KDE scroll bars I'd be fine, but the icons look hideous in Unity. By the way, when you used Xubuntu, did it mess with the icons/style in Unity? If so, how did you fix it?

---

### Post by Bucky Ball on 2015-11-16
I don't use Ubuntu or Unity. I do a minimal install and install xfce4. I don't use a default set up from any flavour.

If you installed xfce4 to try in Ubuntu, yes, I imagine it would add its own icons, etc, to your choices. This is not interference. This is exactly what would be expected to happened.

---

### Post by jonathan90 on 2015-11-17
So I followed the tutorial on [this website]("http://askubuntu.com/questions/177909/restore-gtk-integration-after-removing-kde") and moved the Oxygen and KDE themes/icons to a different folder and my scroll bars/right click stuff is back to normal. However, the fonts still look really thin and skinny for some reason. Any ideas? [Here's a screenshot]("http://imgur.com/mmiiFvL") of the fonts I'm talking about.

And by the way, what's a minimal install?

---

### Post by Bucky Ball on 2015-11-18
My favourite question. A minimal install installs the Ubuntu kernel only, you add the rest! :D This way you can install only what you want/need and the desktop environment you like. Few moving parts, light and fast. 

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

You can mix and match and create a hybrid. I use xfce4 DE and pcmanfm for file manager, lxterminal for terminal, Firefox, Synaptics, Thunderbird, Libreoffice, Gimp. Few other assorted bits and pieces. xfwm and lightdm for window manager and desktop. 7.5Gb install, personal data on another partition.  

Back to the topic, as for your font, have you tried just choosing another from something like Settings> Appearance (or Desktop)?

PS: Nice one nutting out the other stuff. ;)

---

### Post by PaulW2U on 2015-11-18
> **jonathan90 said:**
> I installed it using 
```
sudo apt-get install kubuntu-desktop
```

 and I tried using 

```
sudo apt-get remove kubuntu-desktop
```

but it didn't remove anything.

That's because kubuntu-desktop is a [meta package]("https://help.ubuntu.com/community/MetaPackages") which if installed will pull in dependencies but if removed will do nothing as you found out.

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)
[http://askubuntu.com/questions/451620/how-to-completely-remove-kubuntu-desktop-from-ubuntu](http://askubuntu.com/questions/451620/how-to-completely-remove-kubuntu-desktop-from-ubuntu)

are two links that might have helped with older versions Ubuntu/Kubuntu so I'm **not** recommending that you execute any of the commands but take a look to get an idea of what needs to be done when two desktops are installed at the same time and one needs to be removed. I really wish this wasn't possible and that the dependencies were set to disallow it. :(

I have a test laptop that I have successfully changed as follows:

Xubuntu 15.04, Xubuntu 15.10, Ubuntu 15.10, Ubuntu 16.04, Ubuntu GNOME 16.04

In each of those conversions, rather than the upgrades, I have to do a great deal of searching with something like aptitude or synaptic to remove unwanted packages. It wasn't easy, took a great deal of time and I probably still have something that is not what I would have had had I installed Ubuntu GNOME from the outset.

One thing that you could try in a terminal is:
```
sudo apt-get install ubuntu-system-settings --reinstall
sudo apt-get install ubuntu-settings --reinstall

```
Those commands won't remove Kubuntu or any KDE packages of course but they may restore some Ubuntu defaults.

Hope that helps. Good luck.

---

### Post by jonathan90 on 2015-11-18
What are exactly are ubuntu-system-settings and ubuntu-settings? I ran the first command and it took a while to do load and so I stopped it cause I was worried I'd mess something up.

---

### Post by Bucky Ball on 2015-11-18
Stopping it halfway through has a good chance of messing it up. :)

Those things should be there. You are only reinstalling them to make sure they are.

---

### Post by jonathan90 on 2015-11-19
Well so far my OS hasn't broken yet (and hopefully never will).  Should I use dpkg --reconfigure for ubuntu-system-settings?

Also, I figured out how to get the fonts back to normal. I took fonts.conf from etc/fonts and made a copy of it in home/.config/fontconfig. Now KDE and Ubuntu's fonts seem seem to coexist without either overwriting the others' font configuration! 

Only thing now is that the GRUB menu is black instead of purple and it has the Kubuntu boot screen instead of Ubuntu (this happened right after I got KDE). Just wondering, is that a system error? Last time GRUB was black instead of purple, my entire Ubuntu OS was corrupt.

---

