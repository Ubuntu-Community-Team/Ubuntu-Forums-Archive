---
title: "Reinstall Xorg?"
date: 2006-10-01
forum: Desktop Environments
---

### Post by Inverted on 2006-10-01
Hi all,

I have been trying to get beryl & XGL to run Dapper. I think i have inadvertently removed/unistalled either the X window system or Xorg. I have been getting the following messages when running

> sudo dpkg-reconfigure xserver-xorg

This results in the Error message 
> 
Fatal server error
Can't Find Xorg executable

I also get this error message when I try to run it again.
> 
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.2006101155222

I know it's something daft that I have done, but I can't with my limited knowledge of Linux quite track it down.

Obviously I can only run in terminal at the mo, Is there a way to reinstall Xorg using apt-get from the command line? 
I don't want to reinstall if I can, as I am sure there is a way around this. 

I am running Ubuntu Dapper Drake
My system is as follows

Asus A7N8X M/board 
Athlon XP3000+
Nvidia Geforce FX5600 256mb
1gb ram

Thanks in advance

#Edit - I tried to launch beryl from command line and got the following message.
(beryl-manager:19680) Gtk-WARNING **: cannot open display:

---

### Post by christhemonkey on 2006-10-01
Try the following:
```
sudo apt-get install ubuntu-desktop 
```
That should re-install a fully featured desktop system for you without losing all your files with a full reinstall.

NB Launching beryl from a command line wont work as it requires an X server to be running.

---

### Post by Inverted on 2006-10-01
Hi,

Thanks for the help. I just tried your suggestion, but I get back a message saying that ubuntu-desktop is already the newest version, so I tried sudo apt-get update and sudo apt-get dist-upgrade. I then tried again, but it still reports the latest version.
I rebooted for good measure and ran reconfig for xorg, but I still get a message saying
> 
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf

Thanks again

---

### Post by christhemonkey on 2006-10-01
Try this:
```
sudo apt-get install ubuntu-desktop --reinstall 
```

---

### Post by Inverted on 2006-10-01
Just tried the reinstall, but still no success
I am getting the same message as before, and it  still says it can't find Xorg executable.

---

