---
title: "Installing VNC on Ubuntu 10.10 Server"
date: 2011-06-23
forum: Desktop Environments
---

### Post by Ostrichmeat on 2011-06-23
Hi guys,

I have been trying to get Gnome and VNC installed on Ubuntu 10.10 Server 64 bit which is running on a VPS which I have no physical access to (only SSH). I have successfully done this on CentOS before (using guides I found through Google) but I cannot seem to get it set up in Ubuntu.

First of all, I have good reasons for needing a *full* GUI via VNC on my VPS. I am aware of the security implications. Like I said, I have done this before on CentOS, but I want this machine to use Ubuntu as I need a Debian environment.

So far, I have clean installed, then installed the desktop environment by:

```
sudo apt-get install ubuntu-desktop
```Then I have created a sudoer user through which I installed vnc4server following instructions on [http://usingnix.wordpress.com/2010/12/15/setup-vnc-in-ubuntu-10-10/](http://usingnix.wordpress.com/2010/12/15/setup-vnc-in-ubuntu-10-10/)

I have tried a variety of tweaks since then but the closest I have managed to come to connecting to VNC is a grey VNC window (of the correct geometry that I specified), with a black pattern with the X mouse pointer which moves around.

I know I can't be far off with this, but I am not getting Gnome or the software installed. I am using TightVNC on my local Ubuntu machine to connect.

Any help would be greatly appreciated!

---

### Post by Ostrichmeat on 2011-06-23
Screen shot of what I am getting in TightVNC here:

[http://www.markmearns.com/screenshot.jpg](http://www.markmearns.com/screenshot.jpg)

---

### Post by Ostrichmeat on 2011-06-23
More hours of Google search led me to this article:

[http://help.cinfu.com/gui-desktop-xwindows-gnome-installation-on-linux-vps-server-with-ubuntu-os-37/](http://help.cinfu.com/gui-desktop-xwindows-gnome-installation-on-linux-vps-server-with-ubuntu-os-37/)

Absolutely brilliant step-by-step article on how to do exactly what I wanted.

---

