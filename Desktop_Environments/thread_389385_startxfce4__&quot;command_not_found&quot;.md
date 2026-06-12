---
title: "startxfce4:  &quot;command not found&quot;"
date: 2007-03-20
forum: Desktop Environments
---

### Post by Brendantb on 2007-03-20
Hi, 

I have been trying to do a minimal install of the latest Xfce4.4 on a command line installation of xubuntu. 

The command line installation went well, and I can login to the console. I have a good internet connection going. 

I downloaded the following packages: 

xubuntu-desktop (from ubuntu.tolero.org)
xorg
xubuntu-system-tools

If possible, I wan't to avoid using gdm, or any other desktop manager. I have been using this as a guideline: 

[http://wiki.xfce.org/faq](http://wiki.xfce.org/faq)

The problem is that there isn't a startxfce4 command, and I can't figure out what package I should download to get it. 

Any pointers would be appreciated.

---

### Post by kerry_s on 2007-03-20
Okay your going about it the wrong way.

do the server/command-line install
login to the command-line
sudo su
nano /etc/apt/sources.list
make sure you uncomment all the repos
ctrl and x and y and enter to save
apt-get update
apt-get install xorg gdm xfce4 leafpad synaptic
reboot
select xfce4 from the session menu and log in

You should be in a bare bones install, use synaptic to get what ever else you want installed.

---

