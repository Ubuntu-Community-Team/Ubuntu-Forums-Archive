---
title: "4  (or 8) desktops on LXDE, ubuntu 16.04"
date: 2017-10-28
forum: Desktop Environments
---

### Post by vanhelmont on 2017-10-28
Hi, my newly installed LXDE on ubuntu 16.04 server (Why didn't I just install lubuntu? It, xubuntu, ubuntu desktop, mint, and fedora all fail in the installation process, but ubuntu server with ncurses installs fine) presents a proper login screen, but then when I log it it displays what looks like 4 squished desktops across the top of the screen, with what looks like 4 login screens under that, then the bottom half just purple.  I'm thinking maybe there's a configuration file somewhere to tell it about how many pixels the monitor has? It's an old spire 17 monitor from a thrift store, but seems to be working fine.  

I have an AMD APU, I think it's an A6 if I remember, but the gigabyte bios doesn't tell much, but lspci said "Beavercreek" I think it's radeon 6520.

I did 

sudo apt-get install lxde

and the only other things installed are LAMP and OpenSSD

Any suggestions will be appreciated!

---

### Post by vanhelmont on 2017-10-28
I fixed it! added a line to /etc/xdg/lxsession/LXDE/autostart,

@xrandr --output VGA --mode 1280x1024

and I have a single desktop displayed properly!  A plain black screen,
but I'm sure it's not hard to change that.

---

