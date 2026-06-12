---
title: "Problem installing Gnome3 on unbuntu  maverick"
date: 2011-09-18
forum: Desktop Environments
---

### Post by sptutusukanta on 2011-09-18
**I wanted to install gnome3 on maverick. I got this tutorial here:** 
[http://www.wiredrevolution.com/ubuntu/install-gnome-shell-in-ubuntu-10-10-maverick]("http://www.wiredrevolution.com/ubuntu/install-gnome-shell-in-ubuntu-10-10-maverick")

But after running the command:
```
./gnome-shell-build-setup.sh
```
I got an error:
```
Please run 'sudo apt-get install libxcb-aux0-dev libxcb-event1-dev accountsservice libx11-xcb-dev libwebkitgtk-3.0-0 libsane-dev libgudev-1.0-dev libical-dev gperf ' and try again.
```

As suggested I run the command:
```
sudo apt-get install libxcb-aux0-dev libxcb-event1-dev accountsservice libx11-xcb-dev libwebkitgtk-3.0-0 libsane-dev libgudev-1.0-dev libical-dev gperf
```
Got another Error: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package accountsservice
E: Unable to locate package libwebkitgtk-3.0-0
E: Couldn't find any package by regex 'libwebkitgtk-3.0-0'
```

**What can I do to solve this issue?**

---

### Post by xinfin on 2011-09-22
Hi i've got the exact same problem here. Please can anybody help? Thanx in advance. x.

---

### Post by Krytarik on 2011-09-22
> **sptutusukanta said:**
> **What can I do to solve this issue?**
> **xinfin said:**
> Hi i've got the exact same problem here. Please can anybody help?
You both, why don't you just download the Beta 2 of Oneiric 11.10 - or wait until it's released on October 13th!?
Much easier and much more stable option!

[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview)

Greetings.

---

### Post by jerrrys on 2011-09-22
[http://ubuntuforums.org/showthread.php?t=1848031](http://ubuntuforums.org/showthread.php?t=1848031)

---

### Post by adi_30stm on 2011-11-13
Umm.... i had the same problem ...the file missing you can install them through Ubuntu Software Center by copying n pasting them one by one in the search. I think you might have to add the gnome repo to the other software list  [COLOR=#008080]*sudo add-apt-repository ppa:gnome3-team/gnome3*[/COLOR]

---

### Post by MARP1961 on 2011-11-13
There really is little point in playing around trying to get Gnome 3 on Maverick (or even for that matter the much easier Natty 11.04). You simply need to do a fresh install of the latest 11.10 Oneiric Ocelot or (if you are brave) a Distribution Upgrade first to 11.04 then to 11.10.

If you do this then Gnome 3 will be the system you have without any need to play around with buggy workarounds. If you don't like the default Unity desktop, then just install Gnome and try logging into it to experience Gnome Shell. If that doesn't do it for you then install Xubuntu Desktop. The possibilities and alternatives are many but don't waste time and effort on trying to get Gnome 3 to work on outdated versions.

---

