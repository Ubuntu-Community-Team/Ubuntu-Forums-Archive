---
title: "Failed to start X server"
date: 2006-01-06
forum: Desktop Environments
---

### Post by Ubluntu on 2006-01-06
I'm not sure if its something as simple as a Mac panther type gnome theme i installed, switching to 1600x1200 (which I have had it set to before), or running x2vnc( to move mouse to a win machine ) Right before it did this I had x2vnc running and changed to 1600x1200, x2 messed up and left a black line where my old resolution would have been...
 
When I rebooted I get:
 
Failed to start X server, would you like to see X server output to diagnose?
 
When I hit yes I get: X win server 6.99.99.904 ( 7.0.0 RC 4 )
build os linux 2.6.10 i686
current os ubuntu 2.6.15-10-386
 
I went into /etc/X11/xorg.conf and changed i810 to vesa, and changed PCI:0:2:0 to 1:0:0 (what is this, i assume it should be 1:0:0 from other posts but...)
 
No luck.. but I noticed at GRUB there is a new kernel, now there is a 2.6.10 and a 2.6.8 when I run the 2.6.8 i see something flash about 2.6.15 i think...
 
If I do 2.6.8 recovery, at the shell I type startx and get:
dlopen /usr/lib/xorg/modules/extensions/libGLcore.so
Failed to load "GLcore" ( loader failed, 7 )
No device detected
 
Fatal error
No screen found
x10: fatal IO error 104 ( connection reset by peer ) x[SIZE=1](or unix or somin)[/SIZE] server ":0.0"
 
Then about 10 seconds later, after typing startx or when i get the Failed to start x server on regular boot this just gets printed on the screen where ever the cursor is:
 
syslogd: /dev/xconsole: No such file or directory
 
This sucks! 
I was LOVING ubuntu up to this, install was Awsome, better then XP! I was watching tv and running PHP and MySQL pages within like 2 hours of poping the CD in.
 
I really don't want to re-install, i'm installing on another machine and actually having problems getting GRUB to install(thats another post) but I am not comfortable LiveCD-ing into this broken X server install and backing up files, I never finished setting up so I dont really know where everything is..
 
Anyway, is this X server stuff the same on all linux and not only ubuntu?? Does anyone know an X server forum I can try?
 
I was also trying to get MythTV working before this happened, which needed Make and a bunch of other crap that I didn't get working, I don't believe I did anything there that would have caused this.
 
Thanks in advance, I would love to get this ubuntu working again and look foward to being a part of the ubuntu community Awsome work guys!=D>

---

### Post by mo_x on 2006-01-06
Execute the following command to reconfigure your xorg.conf:
sudo dpkg-reconfigure xserver-xorg

Changing PCI:0:2:0 to PCI:1:0:0 was not a good idea. That is the BusId of your graphics card and is not the same for everyone. You can check the BusId with the command lspci.

---

### Post by Ubluntu on 2006-01-06
I tried the reconfigure stuff, read a few posts about it, the PCI stuff only gives me these errors when I do 1:0:0:, if i do anything else it gives me a different error that seems to be because it can't find a graphics card.

---

### Post by mo_x on 2006-01-06
It is not clear to me what errors you are getting and when you are getting them.
Please post the output of the lspci command.
Post as attachements your /etc/X11/xorg.conf and /var/log/Xorg.0.log files.
Can you unistall x2vnc?

---

### Post by Ubluntu on 2006-01-06
Going to try the Ispci and read the log files now. I didn't install x2vnc so I don't know how to uninstall without the package manager.
 
I doubt it makes a difference but: This is a intel 865(i think) mobo with on board video. This is what I was using when it crashed, i also tried an nvidia AGP card and had same results
 
ADDED:
x2vnc is started manually by me after gnome is done booting, I don't think its causing a problem, but i guess it is possible

---

### Post by Ubluntu on 2006-01-06
I'm writing from my ubuntu install!!

Not exactly sure what I did, but my xorg.conf file now has Driver "vesa" & Option "NoAccel" and I changed PCI 1:0:0 back to 0:2:0
Right after saving xorg.conf and running startx, my screen loaded the intel bios splash screen all messed up, and ubuntu loaded with a repeating line background and logged in as a limited user I don't believe exists on the machine.

Then I rebooted and it logged in normal with this in the middle of my desktop:

Internal Error: FAMOpen() failed make sure fam/gamin is installed. 

I was unable to click anywhere, I Ctrl - Alt - Backspaced and it flashed a black screen and went back to my login, where I logged in, shit myself because it worked and started writing here.

I can upload my log files now since I am writing from ubuntu( assuming ubuntu still works after a restart) does anyone think that would help determin what went wrong here??

What did go wrong here? This problem was pretty annoying and would have left an average user reinstalling ubuntu which is not cool. I would like to help figure out how this happened, even if requires breaking my install again.

I disabled the Mac Panther theme I loaded before crash, my screen is at 1024x768 because of the dpkg-reconfig i did, and x2vnc isn't running yet. Please! Why did this happen?

---

### Post by mo_x on 2006-01-06
First make a backup of your working /etc/X11/xorg.conf.

---

### Post by Ubluntu on 2006-01-06
What do you mean first make a backup? Before I start trying to break it again, or you would like to view it? Thanks

---

### Post by mo_x on 2006-01-07
Before you do some more experimenting, then you have something to fall back on :)

---

