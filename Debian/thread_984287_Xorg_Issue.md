---
title: "Xorg Issue"
date: 2008-11-16
forum: Debian
---

### Post by napalm brain on 2008-11-16
I just installed Etch on my box and whenever I boot into Debian, the screen blinks (at this point I knew what was about to happen), and a dialog pops up stating there has been an error in Xorg and "No Screens Have Been Found."

First, I know I need to edit the /etc/X11/xorg.conf and do the /etc/init.d/gdm restart.. the usual stuff but I always get hung up from there. Is there anyway to make Etch compatible with my graphics card? And further from this, is it possible to have the correct screen resolution? 

Help would be greatly appreciated. :)

---

### Post by p_quarles on 2008-11-16
Well, what graphics card are you using?

---

### Post by napalm brain on 2008-11-16
I guess I forgot an important detail. :oops:

GeForce 8400M GT

BTW, one thing I am not sure of is how to get the output from the what went wrong. I feel that's another detail that would help immensely.

---

### Post by p_quarles on 2008-11-16
Well, make sure you have the Xorg driver installed:
```
# apt-get install xserver-xorg-video-nv
```
I don't have much experience with that card, but I'm hoping that will get any missing kernel modules as well.

To get more info, I would start by doing this (from a CLI console)":
```
echo "gnome-session" > ~/.xinitrc
startx
```
See what happens at that point.

---

### Post by napalm brain on 2008-11-16
Quick question before I try it: how do I run as a super user? I tried to use sudo, but it stated that my user name was not in the sudoers file and I wasn't sure if there was a work around to that..

---

### Post by wirespot on 2008-11-16
Try looking in /var/log/Xorg.0.log for errors.

---

### Post by p_quarles on 2008-11-16
> **napalm brain said:**
> Quick question before I try it: how do I run as a super user? I tried to use sudo, but it stated that my user name was not in the sudoers file and I wasn't sure if there was a work around to that..
Debian isn't configured to use sudo by default. Ubuntu is fairly unique in that regard.

To run a command as root:
```
su -c command
```
To run a root shell:
```
su -
```
To add your user to sudoers:
```
su -c visudo
```
and add a line like:
```
%admins ALL=(ALL) ALL
```
Then save that and run:
```
su -c 'adduser $USER admins'
```
You will need to logout and back in before the change takes effect.

---

### Post by napalm brain on 2008-11-16
I edited the /etc/X11/xorg.conf file and changed the card to "vesa" so I could actually enter the system. 

The aptitude install xserer-xorg-video-nv had already been installed and did not affect anything, unfortunately. Nothing seemed to happen on the echo command either.

---

### Post by p_quarles on 2008-11-16
> **napalm brain said:**
> I edited the /etc/X11/xorg.conf file and changed the card to "vesa" so I could actually enter the system. 

The aptitude install xserer-xorg-video-nv had already been installed and did not affect anything, unfortunately. Nothing seemed to happen on the echo command either.
The "echo" command just configures the xinit resource file. startx is what should actually do something.

---

### Post by napalm brain on 2008-11-16
startx basically said the same thing as the error message from before. I reconfigured the /etc/X11/xorg.conf so the driver was named "nv," as it originally was.The "fatal error: no screens were found" was prompted again.

---

### Post by wirespot on 2008-11-17
Please copy /var/log/Xorg.0.log somewhere else immediately after this happens, then gzip it and post it here.

---

### Post by napalm brain on 2008-11-18
Here is the file. Thank you all for all your help. I really appreciate it.

---

### Post by napalm brain on 2008-11-18
I would edit the last post but I managed to come out with a solution.

I became a "big boy," so to speak, and managed to figure out the problem. I manually installed the NVIDIA driver and alls well that ends well. I couldn't have done it without some of the guidance from all of you though. Thank you very much.

This is ultimately where I found the solution:
[http://http://www.pendrivelinux.com/2007/10/27/how-to-install-nvidia-video-card-drivers-in-debian-lenny/]("http://http//www.pendrivelinux.com/2007/10/27/how-to-install-nvidia-video-card-drivers-in-debian-lenny/")

---

### Post by basenvironment on 2008-11-19
probably should of checkd out
[http://wiki.debian.org/NvidiaGraphicsDrivers](http://wiki.debian.org/NvidiaGraphicsDrivers)
and/or
[http://forums.debian.net/viewtopic.php?t=10812](http://forums.debian.net/viewtopic.php?t=10812)

---

