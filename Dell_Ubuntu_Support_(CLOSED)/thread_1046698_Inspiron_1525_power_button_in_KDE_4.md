---
title: "Inspiron 1525 power button in KDE 4"
date: 2009-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ScottyDelicious on 2009-01-21
Last spring (may 2008 ) I bought an Inspiron 1525n from Dell with Ubuntu 7.10 preinstalled. I bought this as a cheap laptop to get to know Linux better, but it has quickly torn me away from Mac OS X and my MacBook Pro and now, this cheap little Dell with Ubuntu is my primary machine. I do everything on this computer.

I decided that I wanted to extend the areas of my expertise to include KDE ( :p ), so I installed the kubuntu-desktop meta package. It is pretty cool, but there are a few things making it hard for me to keep an open mind and approach this objectively. The main thing is that, in Gnome (Ubuntu 8.10), when I press the power button on my laptop, gnome-power-management opens a very handy dialog window allowing me to select what I want to do (Shut down, restart, suspend to ram, or hibernate). When I am going to be AFK for a while, I have formed a habit of pressing the power button and selecting "Suspend".

In KDE 4 (4.1 on Kubuntu 8.10, and now 4.2 RC on the Jaunty Alpha) when I press the power button, the computer immediately goes to shut down. This is not what I was looking for. Ideally, what I want is to be prompted when I press the power button so I can select "Suspend to RAM". Of course I could just click the kickoff menu and select it from there, but I tend to use my keyboard, keyboard shortcuts, and launchers MUCH more than the mouse and menus, so this is really taking me out of my element.

I hope this didn't turn into tl;dr.

---

### Post by tomchiverton on 2009-02-26
Snap. Going into system settings, power and setting the right thing there doesn't seem to have any effect :-(

---

### Post by ScottyDelicious on 2009-02-26
I don't think this is an ideal solution, but it does work!

```
cd /etc/acpi/
sudo mv powerbtn.sh powerbtn.sh.disable
```

renaming the ACPI power button script allows KDE to do its normal prompt for some reason. I am still looking into this, however, so this is just a temporary fix.

---

### Post by tomchiverton on 2009-02-27
See [https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/288639](https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/288639) 

I've also attached my replacement /etc/acpi/powerbtn.sh here.

---

### Post by droetker on 2011-07-31
Same here.
Look at [https://bugs.launchpad.net/kubuntu-ppa/+bug/713198](https://bugs.launchpad.net/kubuntu-ppa/+bug/713198).

---

