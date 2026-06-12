---
title: "Virtualbox-only type of machine"
date: 2009-03-19
forum: Desktop Environments
---

### Post by TheGameAh on 2009-03-19
Hey guys.

Was looking to put together a laptop that basically only ran Virtualbox.  It would boot, the user would login, and the first thing that autoloaded would be the VBox interface.

I loaded a copy of Debian down.  Then IceWM, and VirtualBox.  The plan was to put the image on a server, so I could bring it down to any machine.

This actually worked, but a few hiccups have me rethinking things.  There is no applet for wireless networking in IceWM (used to desktop environments, not window managers).  So I'm unsure of what to load to handle laptop devices like wireless, or power management.

Given this, has anyone done something similar?  Any tips?  Was thinking about going with XFCE, as that would let me manage wireless and power better.  But installing XFCE also installs a web browser, open office, etc.

---

### Post by thtrgremlin on 2009-03-19
For the most part, a gui only provides front end support for backend application, except in the rare case where the interface itself is the application (such as Firefox). On the other hand, Kino, as cool as it is, is only a front end to ffmpeg where what you really want to do is edit video.

In this case, you want to connect to a wireless network. part of your start up scripts will need to include networking. The applet is only for user convenience. The simple thing to do is either: ```
sudo /etc/init.d/networking start
```or my personal favorite```
sudo ifconfig eth0 up
sudo dhclient eth0
```or whatever your network device may be. Your settings for /etc/network/interfaces includes everything you want done with regard to network setup when you run '/etc/init.d/networking start'. If you want to get started quickly without getting to know how it all works, use a live CD running ubuntu and set everything using nm-applet. After that, look at /etc/network/interfaces to see what it actually setup with regards to all the different devices, roaming, and such.

I recently customized a machine to only run Firefox, and a custom daemon to keep it from closing, so have done something similar to what it sounds like what you are doing. I used the above mentioned steps for my own terminal project.

Best luck. Feel free to ask if you have any more questions. I typically watch threads for up to 3 days  :)

---

