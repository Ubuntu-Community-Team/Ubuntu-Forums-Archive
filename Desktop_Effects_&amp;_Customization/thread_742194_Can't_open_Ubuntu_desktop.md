---
title: "Can't open Ubuntu desktop"
date: 2008-04-01
forum: Desktop Effects &amp; Customization
---

### Post by bharkins on 2008-04-01
On my HP notebook have been working with Compiz and Awn, and yesterday thought I had most of it working OK. Today, I tried to get to the desktop and only went through the password and then hung on the Ubuntu orange screen. What keystrokes can get to a terminal and what command to restore Gnome desktop? 

[Note: on my desktop machine today I am getting pink font headings on the Forum. Is this intentional or only my machine?]

---

### Post by alan34 on 2008-04-01
Ctl-Alt-F1 will get you to terminal login.

Backup your existing xorg.conf file

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

This command will restore your desktop but it will remove all special graphics settings
for example Nvidia/ATI drivers.

sudo dpkg-reconfigure -phigh xserver-xorg

Then restart

sudo shutdown -r now

---

### Post by bharkins on 2008-04-01
> **alan34 said:**
> Ctl-Alt-F1 will get you to terminal login.

Backup your existing xorg.conf file

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

This command will restore your desktop but it will remove all special graphics settings
for example Nvidia/ATI drivers.

sudo dpkg-reconfigure -phigh xserver-xorg

Then restart

sudo shutdown -r now

Tried it - no go. I also tried 

sudo apt-get install ubuntu-desktop

That looked promising except to a point where I received error messages:

"Can't resolve http://us.archive.ubuntu.com/...." following all the Gnome file names. On my desktop machine, the URL was good for the files that were trying to download.

I've now spent more time searching the Net for this solution which is far more than to reinstall apps. compiz, awn, etc. However, the search for answers is part of the Ubuntu adventure (?)

---

### Post by alan34 on 2008-04-02
Can you get to the recovery consol from the Grub menu. Will that start? You should be able to run
sudo dpkg-reconfigure -phigh xserver-xorg from there.

If you only have Ubuntu on your PC and there is no actual Grub menu appearing, hit the Esc key when you see the Grub flash up on the top right of the screen and you should then be presented with the Grub menu to pick the recovery consol.

Hope this helps

---

### Post by bharkins on 2008-04-02
> **alan34 said:**
> Can you get to the recovery consol from the Grub menu. Will that start? You should be able to run
sudo dpkg-reconfigure -phigh xserver-xorg from there.

If you only have Ubuntu on your PC and there is no actual Grub menu appearing, hit the Esc key when you see the Grub flash up on the top right of the screen and you should then be presented with the Grub menu to pick the recovery consol.

Hope this helps

Thanks, but I went ahead and am currently reinstalling Hardy. My HP machine config is shown in the signature and it is strictly a test platform. However, I am interested in being able to solve such a problem as I have now installed Gutsy on my desktop machine and getting ready to set up Thunderbird for daily use. I would hate to have Ubuntu freeze up as before and not be able to restore with all settings intact.

---

