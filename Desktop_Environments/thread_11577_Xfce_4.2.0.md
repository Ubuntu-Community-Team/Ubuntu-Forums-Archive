---
title: "Xfce 4.2.0?"
date: 2005-01-17
forum: Desktop Environments
---

### Post by Hikaru79 on 2005-01-17
I'm installing it as I type, and I'm just wondering if any other Ubuntu-ers have gotten this new version ahead of me and have any opinions?

---

### Post by MoveZig on 2005-01-17
I installed it yesterday over my previous installation of RC3 using the graphical installer.  Works perfectly.  Haven't used gnome for weeks now...

---

### Post by Darrena on 2005-01-17
[QUOTE=Hikaru79]I'm installing it as I type, and I'm just wondering if any other Ubuntu-ers have gotten this new version ahead of me and have any opinions?[/QUOTE]
 I was considering it, I prefer using Xfce when I am using NX so let us know how it goes!

---

### Post by alucard on 2005-01-18
Works great. I used the os-cillation graphical installer, it now even has option to configure the display manager  :) .

The xfld-desktop debian packages available on the same site do not work though.

---

### Post by Hikaru79 on 2005-01-18
[QUOTE=alucard]Works great. I used the os-cillation graphical installer, it now even has option to configure the display manager  :) .

The xfld-desktop debian packages available on the same site do not work though.[/QUOTE]
 Man, Xfce rules. It's my first time giving it a try, but I think I'm sold. Clean interface, easy installation, and best of all, I'm getting a very noticable speed increase. 

Reccomended to everyone!!

---

### Post by valadil on 2005-01-18
I've been using 4.1.99rc3 for quite some time now.  Haven't noticed any differences between this and 4.2.0.  

I quite like XFCE.  It's basically has all the features of gnome I use and none of the ones I try to ignore.  I don't so much like how the menu is edited, but once you get it set up once it's happy.  XFCE also makes it hard to make adjustments via text files rather than via the built in gui interfaces.  That's not a bad thing, it just takes some getting used to if you like doing htings by hand.

---

### Post by Randabis on 2005-01-18
It's an excellent alternative to gnome, and fits my laptop perfectly (pentium 3 450 mhz, 224mb of ram). I still use gnome on my main box, but the laptop loves xfce. :)

---

### Post by Hikaru79 on 2005-01-20
Here's the only question I have-- I would *really* love to have a "Show Desktop" button that automatically minimizes everything like there is for KDE and GNOME. I haven't been able to find it in Xfce. Anyone have any ideas?

---

### Post by Quest-Master on 2005-01-20
Is there a way to set Keyboard Shortcuts in XFCE as you can in Gnome? (Computer -> Desktop Preferences -> Keyboard Shortcuts -- in Gnome)

---

### Post by Randabis on 2005-01-20
[QUOTE=Hikaru79]Here's the only question I have-- I would *really* love to have a "Show Desktop" button that automatically minimizes everything like there is for KDE and GNOME. I haven't been able to find it in Xfce. Anyone have any ideas?[/QUOTE]

Umm, it has one. If it isn't able to be added to the panel then you might need the goodies pack.

---

### Post by Hikaru79 on 2005-01-22
[QUOTE=Randabis]Umm, it has one. If it isn't able to be added to the panel then you might need the goodies pack.[/QUOTE]


Indeed, the goodies pack has it! Thanks Randabis! Xfce rules!

---

### Post by AndersAA on 2005-01-22
only thing I miss in xfce is nautilus, I like having shortcuts to a few specific directiries on my desktop, so I can open and or drop stuff there.  It took some getting used to, but I've really fallen in love with spatial nautilus.

---

### Post by scotty on 2005-01-22
I am trying to install it myself.

I have apt-get dist-upgrade ed.

The installers from the site do not work for me.

When I use apt-get I get this:
---
scotty@ubox:~ $ sudo apt-get install -t testing xfce4 xfce4-session xfce4-utils xfdesktop4
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xfce4-utils: Depends: libgtkhtml2-0 (>= 2.6.2) but 2.4.1-1 is to be installed
E: Broken packages
scotty@ubox:~ $
---

Help!  I love xfce but I cannot install it.

Scott

---

### Post by CowPie on 2005-01-23
[QUOTE=scotty]I am trying to install it myself.

I have apt-get dist-upgrade ed.

The installers from the site do not work for me.

When I use apt-get I get this:
---
scotty@ubox:~ $ sudo apt-get install -t testing xfce4 xfce4-session xfce4-utils xfdesktop4
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xfce4-utils: Depends: libgtkhtml2-0 (>= 2.6.2) but 2.4.1-1 is to be installed
E: Broken packages
scotty@ubox:~ $
---

Help!  I love xfce but I cannot install it.

Scott[/QUOTE]
 Hi, have you tried to /etc/apt/sources.list

deb [http://www.os-works.com/debian](http://www.os-works.com/debian) unstable main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) unstable main

It worked for me on hoary.

FOr my question: is there anyway to get rid of that horrible XFCE4 panel and just stick it with the taskbar?  I hate the 2 bars on gnome as equally as I do here in xfce.

---

### Post by jensyt on 2005-01-23
Since running Hoary, I've been using XFCE for weeks... I had the beta version of 4.2, and now the full version, and it's worked fine the entire time, besides a few small glitches.

[QUOTE=Quest-Master]Is there a way to set Keyboard Shortcuts in XFCE as you can in Gnome? (Computer -> Desktop Preferences -> Keyboard Shortcuts -- in Gnome)[/QUOTE]
There is something about keybindings in the Window Manager settings. If you go to the Settings dialog, click on Window Manager, and then the tab for keyboard. Personally, I've never used it, so I don't know how good it is at all.

As for XFCE overall - I really like it; I don't use GNOME at all anymore. I don't particularly like that the panel isn't very 'customizable', but I've grown to like its layout.

---

### Post by scotty on 2005-01-23
[QUOTE=jensyt]Since running Hoary, I've been using XFCE for weeks... I had the beta version of 4.2, and now the full version, and it's worked fine the entire time, besides a few small glitches.


There is something about keybindings in the Window Manager settings. If you go to the Settings dialog, click on Window Manager, and then the tab for keyboard. Personally, I've never used it, so I don't know how good it is at all.

As for XFCE overall - I really like it; I don't use GNOME at all anymore. I don't particularly like that the panel isn't very 'customizable', but I've grown to like its layout.[/QUOTE]
 Yep, I had added those two lines to the sources.list before trying the above posted command.  Do I have to upgrade to hoary first?  I am still running warty.  Is it as simple as changing all instances of warty to hoary in sources.list?

Thanks,
Scott

---

### Post by jensyt on 2005-01-23
I wouldn't suggest upgrading to Hoary yet unless you know what you're doing, as it isn't considered stable yet. It will be officially released early in April, which isn't too far.

If you want the latest and greatest, look into [this thread](http://ubuntuforums.org/showthread.php?t=11516) in the [Backports forum](http://ubuntuforums.org/forumdisplay.php?f=47).

---

### Post by gfg on 2005-01-23
I switched to XFCE 4.2 a few days ago, and i absolutely love it.It's easy to use, looks nice and is very fast

---

### Post by scotty on 2005-01-23
I changed all instances of warty to hoary and did an apt-get update.

Then I did the super long apt-get from the above post.  It wanted like 50+ packages, but all seems well.  The xfld stuff got installed.  xfce is now part of GDM.  All seems well.

Does this mean I have a part warty part hoary setup?

Scott Strungis

---

### Post by CowPie on 2005-01-23
[QUOTE=scotty]I changed all instances of warty to hoary and did an apt-get update.

Then I did the super long apt-get from the above post.  It wanted like 50+ packages, but all seems well.  The xfld stuff got installed.  xfce is now part of GDM.  All seems well.

Does this mean I have a part warty part hoary setup?

Scott Strungis[/QUOTE]
 You need to do an apt-get **dist**-upgrade :)  It confused me too at first!  I think it should be on the sticky in the Hoary forum.

---

