---
title: "Starting Point: ubuntu server, Goal: Fluxbox"
date: 2008-09-18
forum: Desktop Environments
---

### Post by shaggy999 on 2008-09-18
I have an old computer (PII 333 Mhz, 160 MB RAM, 4MB Video Card, 4 GB HD) that has been running ubuntu-server as my desktop (this is currently my one and only computer). I have tried Xubuntu before, but it was too resource intensive for my system (read: painfully slow). I have been reading about fluxbox and am interested in trying it out, but I'm unsure as to how to set up the fluxbox environment when my starting point is ubuntu server. Fluxbox doesn't include xorg-server as a dependency despite the fact that it obviously needs xorg-server available to run. So I'm trying to figure out what the minimal set of packages I need to add to get fluxbuntu up and running.

I know I need xserver-xorg and fluxbuntu. Is it necessary to have a graphical login manager? If so, I'd probably prefer xdm as it looks like the lightest weight login manager available. But my preference would be to login at a terminal and only boot into fluxbuntu as necessary.

Also, should installing xserver-xorg and fluxbuntu be automagical or do I have to edit settings to tell xserver to load fluxbuntu?

Thanks in advance for any help.

---

### Post by leef on 2008-09-18
you could always just execute the startx command after logging in or if you would like autologin, I belive that [mingetty](http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/getty-mingetty.html) is the lightest way to support that, to automatically log in to fluxbox after starting x is to edit ~/.xinitrc to read;

```

startfluxbox

```

which will then select fluxbox as the xsession when x starts, if you need a graphical login, I would go with xdm or possibly a frame buffer login manager (I know this exists but I have forgotten it's name).

---

### Post by snowpine on 2008-09-18
> **shaggy999 said:**
> I have an old computer (PII 333 Mhz, 160 MB RAM, 4MB Video Card, 4 GB HD) that has been running ubuntu-server as my desktop (this is currently my one and only computer). I have tried Xubuntu before, but it was too resource intensive for my system (read: painfully slow). I have been reading about fluxbox and am interested in trying it out, but I'm unsure as to how to set up the fluxbox environment when my starting point is ubuntu server. Fluxbox doesn't include xorg-server as a dependency despite the fact that it obviously needs xorg-server available to run. So I'm trying to figure out what the minimal set of packages I need to add to get fluxbuntu up and running.

I know I need xserver-xorg and fluxbuntu. Is it necessary to have a graphical login manager? If so, I'd probably prefer xdm as it looks like the lightest weight login manager available. But my preference would be to login at a terminal and only boot into fluxbuntu as necessary.

Also, should installing xserver-xorg and fluxbuntu be automagical or do I have to edit settings to tell xserver to load fluxbuntu?

Thanks in advance for any help.

Hi Shaggy, it sounds like you are confusing Fluxbox and Fluxbuntu... they are different things. :) Fluxbuntu is a complete distro that uses Fluxbox as its windows manager. Unfortunately, you can't install Fluxbuntu on top of an existing build (like you can by, for example, 'apt-get install xubuntu-desktop'). You can install Fluxbuntu from scratch, or you can install Fluxbox on top of your existing Ubuntu Server build.

Assuming you want to install Fluxbox on top of your existing build, the easiest thing to do is probably:

sudo apt-get update
sudo apt-get install fluxbox xorg
sudo dpkg-reconfigure xserver-xorg
startx

There are some really good threads here on the forums about configuring Fluxbox, getting the menus to work, etc. so do a little research and you will have a fun project. Personally, I've recently switched over from Fluxbox to Openbox, not because of any performance issues or anything, just personal taste.

Good luck!

---

### Post by shaggy999 on 2008-09-19
Whoops. I did not mean to say fluxbuntu. I just meant fluxbox. Well it looks like I got it up and running. Mouse doesn't work, I'll have to troubleshoot that (actually, it may be disconnected since I wasn't using it in a terminal environment). But I now got fluxbox up and running. yay!

---

