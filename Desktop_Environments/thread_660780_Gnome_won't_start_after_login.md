---
title: "Gnome won't start after login"
date: 2008-01-07
forum: Desktop Environments
---

### Post by litterbox on 2008-01-07
Hi 

My Gnome won't start after confirming login, 
Nothing seems to be wrong with the video driver ... I have mouse movement on both screens ;-) 
But nothing loads and eventually I return to gdm 

Ive read the previous threads and tried everything but nothing worked. Im not willing enough to reinstall yet cause There is some data on this pc that is important plus I have everything up and running in that session so I want it back 

Now the only session that starts correctly is the GNOME FAILSAFE ... 
But no matter what I do I can start the normal one.. Just the brownish background and mouse 
and then after a minute or so it returns to GDM with a drumroffle (so sound works too) 

Please help ! 

(previous things I did: I tried installing ubuntustudio-audio and ubuntustudio-video, deinstalled them already but didnt solve the problem. )

---

### Post by mouseboyx on 2008-01-07
When the gnome failsafe comes up try running :
```
gnome-session
```
or
```
gnome-pannel && metacity && nautilus && gtk-window-decorator
``` if gnome-session does not work.

You can also run firefox from the terminal to open firefox if you didn't already know...

To fix the problem press Ctrl+Alt+F2, login and remove gnome and re-install it.

```
sudo killall gdm && sudo apt-get remove --purge gnome && sudo apt-get install gnome
```
Do this at your own risk!
This will purge all config files for gnome and any customizations will be lost!

And if something goes horribly wrong:
```
sudo apt-get install jwm
``` so that you still have a semi workable XSession.

---

### Post by sonofabics on 2008-01-09
Hi,
I have exactly the same problem. I am and have been fighting with ATI drivers to get my radeon9600 working properly (including TV out). Before the logon problem happened i had no success with the restricted nor the downloaded ati drivers so i put back the xorg-ati package to be able to use my card above 600x800 vesa mode. 
rebooted, logon screen looks ok 1280x1024 and when i put the password empty screen comes up and after 10-15 seconds i get back to the login screen. I can use GNOME safe mode only.

I tried the above mentioned commands, but it said gnome panel loaded i assume since i could load gnome safe mode.I dont want yet to reinstall gnome there should be a way to reconfigure it.

I think the problems are with the presession startup scripts which i am not able to find yet, and dunno how could see the log of the problem.
I'll keep on googling but if someone has experienced this and has some suggestions it is highly appreciated!

---

### Post by sonofabics on 2008-01-10
Got it working again...
After trying couple of things here is what helped:

sudo dpkg-reconfigure xserver-xorg

It turned out i had the problem with the X server config. Now even ATI's restricted driver is working with the new settings. Probabaly H/Vsync had not been set earlier :( but thats offtopic:)
If you still have the problem try it, but just to be sure backup your current xorg.conf before like this:

sudo cp /etc/xorg.conf /etc/xorg.conf.mybackup

cheers

---

