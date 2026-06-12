---
title: "Ubuntu server minimal desktop"
date: 2013-01-24
forum: Desktop Environments
---

### Post by prem1er on 2013-01-24
Hi. I have been running Ubuntu 10.04 for some time and I'm looking to upgrade the hardware on my server. I would like to also take this time to upgrade my Ubuntu version as well. Currently I'm running on a very minimal GUI desktop environment which allows me to remote connect through NXNomachine or connect a monitor if I need. I'm interested in the same configuration on my new hardware, but don't want to have to deal with Unity. Two questions. It looks like 12.04 is the next LTS version available to me. Can I install a minimal Gnome desktop on this version without Unity? Can I install a Gnome desktop and then remove Unity? What other options are do I have? TIA

List of packages currently used for my desktop

```

xorg
gnome-core
gnome-media
gnome-system-monitor
gnome-applets
gnome-system-tools
gnome-utils
gnome-app-install
sysv-rc-conf
gdm
```

---

### Post by tgalati4 on 2013-01-24
If you want an LTS release then I would install Linux Mint 13 Mate.  It's a gnome2 environment and you can use X-forwarding (ssh -2 -Y) to run mate-panel on another machine to perform your configuration or just use as a another machine.  It runs well on older hardware.

---

### Post by sudodus on 2013-01-24
Other alternatives if you want a light-weight desktop with Ubuntu Server 12.04 LTS are

- XFCE with 3 years LTS until April 2015
```
sudo apt-get install xfce4
```

- If you like the old gnome 2 style with 5 years LTS until April 2017, and are willing to do some tweaking, there is also kansasnoob's desktop environment according to this link
 
[http://ubuntuforums.org/showthread.php?t=1966370]("http://ubuntuforums.org/showthread.php?t=1966370")

---

### Post by prem1er on 2013-01-24
> **tgalati4 said:**
> If you want an LTS release then I would install Linux Mint 13 Mate.  It's a gnome2 environment and you can use X-forwarding (ssh -2 -Y) to run mate-panel on another machine to perform your configuration or just use as a another machine.  It runs well on older hardware.

Trying to stay with Ubuntu if at all possible. Hardware is new.

---

### Post by ibjsb4 on 2013-01-24
Gnome-core is not very minimal.

[http://packages.ubuntu.com/precise/gnome-core](http://packages.ubuntu.com/precise/gnome-core)

I too like to keep it all ubuntu.  Heres where I start with a 12.04 install.

```
sudo apt-get install lightdm gnome-terminal synaptic && sudo apt-get install --no-install-recommends gnome-session-fallback
```

Without the recommends gnome fallback (classic) is pretty light.

[http://packages.ubuntu.com/precise/gnome-session-fallback](http://packages.ubuntu.com/precise/gnome-session-fallback)

NOTE:  Gnome fallback package seems to have been redone today.  Not near as many depends in it and unity seems to also been removed.  So it may be ok to just this package with the recommends.  I really don'\t know for sure since this package just changed.

Also if you use this setup the panel background color needs to be changed to see the menu.

---

