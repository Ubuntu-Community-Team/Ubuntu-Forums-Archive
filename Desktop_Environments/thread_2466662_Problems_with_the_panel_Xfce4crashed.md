---
title: "Problems with the panel Xfce4/crashed"
date: 2021-09-02
forum: Desktop Environments
---

### Post by al53 on 2021-09-02
Hello,

I installed Xfce4 as soon as I installed Ubuntu. Later I removed an icon from the panel and when I rebooted the system it came without the panel, I went to the terminal and reinstalled xfce4,

```
sudo apt-get update
sudo apt install xfce4
```


 But it doesn't come back, this is a screenshot:

---

### Post by cmcanulty on 2021-09-02
try installing xfce4-panel also in synaptic search for panel as you may want or need  a few other things. Then right click panel and the panel preferences and you can add more panels. I have 3 top, bottom and side as I use them to access everything
also under panel preferences at top you can click backup and restore

---

### Post by al53 on 2021-09-02
[CODE][/root@keos-Inspiron-3583:~# LANG=C apt install xfce4-panel
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
xfce4-panel is already the newest version (4.16.2-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@keos-Inspiron-3583:~# 
root@keos-Inspiron-3583:~# LANG=C apt install xubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
xubuntu-desktop is already the newest version (2.237).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@keos-Inspiron-3583:~# 


CODE] :(

---

### Post by ajgreeny on 2021-09-02
What errors, if any, do you see if you try to start the panel with command ***xfce4-panel***

Perhaps it has somehow been removed from the autostart list.

---

### Post by monkeybrain20122 on 2021-09-02
If you want xfce you should just install xubuntu. Installing xfce in standard Ubuntu (gnome) is not that great an idea. While it is possible to install different DEs (and some people claim they have 4 in the same system), it is not a good idea, aside from pulling in a lot of duplicated libraries and apps it also create unforeseen instabilities, you often need some tweaks for this to work smoothly.

---

### Post by al53 on 2021-09-03
Hello there,

All that (xubuntu, etc) and more was tried without any result, even a command that refreshed the panel and made it to return "worked" but when restarting it disappeared again.

The truth is I got tired of battling with the system, there is an instability in it, it is not the same as before (I had it installed a few years ago and the whole thing worked much better then now).

Uninstalled. Thank you for your interest in answering. ):P

---

### Post by guiverc on 2021-09-03
I'm a lover of multiple desktops installed (*but will admit there are issues, especially when you pile many of them together*; *three** on this system**; lubuntu, ubuntu & xubuntu*)  however I gave up just installing individual *[meta-]*packages (like `xfce4`) and decided it was easiest with everything (ie. `xubuntu-desktop`) then removing what I don't want or need.

(*you could always look at what gets included in xubuntu-core; eg. [https://unit193.net/xubuntu/core/xubuntu-21.04-core-amd64.iso.manifest](https://unit193.net/xubuntu/core/xubuntu-21.04-core-amd64.iso.manifest) ; but I got lazy & just used the full desktop package for all as found it easiest*)

If you pick just a metapackage (eg. [https://packages.ubuntu.com/hirsute/xfce4](https://packages.ubuntu.com/hirsute/xfce4)) I've found what is required for one release for it to work, can vary with other release(s).  The various teams (eg. Xubuntu in this case) tend to work and test specific images, the main image uses `xubuntu-desktop`(everything) thus why I've gone for that.

You mention crash; if so looking at crash dumps in /var/crash/ can be helpful

---

