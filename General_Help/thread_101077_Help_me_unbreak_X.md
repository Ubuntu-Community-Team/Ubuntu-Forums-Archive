---
title: "Help me unbreak X"
date: 2005-12-09
forum: General Help
---

### Post by Mosey on 2005-12-09
SO!

I was attempting to enable the xcompmgr neat little trick things and I ended up breaking X when I edited /etc/X11/xorg.conf

I know exactly what I did wrong. It was a careless mistake. Now I get an error when I restart my computer.

Is there anyway to reset my X settings to undue the stupid shit i did.

---

### Post by Ocxic on 2005-12-09
do you just get an error or do you get to a blank login screen?

if you get a login screen then login with your usual user/pass combo and when you get to a shell type

sudo nano /etc/X11/xorg.conf

if you know exactly what you did wrong then this will bring up your xorg.conf for you to edit  hit ctrl-x and yes to save then enter to write to the file.

type startx and X will start and you will know if you fixed it

If that still doesn't work, and you made a copy of your xorg.conf befor you made changes (I hope you did) then just type

sudo cp "path to your backup" "/etc/X11/xorg.conf

example:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

and that will restor your backup

---

### Post by Mosey on 2005-12-09
I get an error saying it can't load because I messed up the code...I know exactly how too

so it take me to the blank login screen. (White text on a black screen)

I login...and attempt to gedit and fix my x config file...

It can't do it.

I have an essay due in the morning...this is such a bad friggin time for this to happen!!!

---

### Post by sami83 on 2005-12-09
[QUOTE=Mosey]I get an error saying it can't load because I messed up the code...I know exactly how too

so it take me to the blank login screen. (White text on a black screen)

I login...and attempt to gedit and fix my x config file...

It can't do it.

I have an essay due in the morning...this is such a bad friggin time for this to happen!!![/QUOTE]

Make sure you are using "sudo" as in

```
sudo nano /etc/X11/xorg.conf
```

PS. Gedit even work trough console?

---

### Post by Mosey on 2005-12-09
when I open the nano editor for xorg.conf I get a blank page...

There is nothing in the file...or that's what it's telling me.

...damn.

---

### Post by codejunkie on 2005-12-09
[quote=Mosey]SO!

I was attempting to enable the xcompmgr neat little trick things and I ended up breaking X when I edited /etc/X11/xorg.conf

I know exactly what I did wrong. It was a careless mistake. Now I get an error when I restart my computer.

Is there anyway to reset my X settings to undue the stupid shit i did.[/quote]
if your wanting to undo your most recent changes try this. 
if you can start the xserver and login to gnome try this open a terminal and enter this command ```
sudo gedit /etc/X11/xorg.conf~
```click on file then Save As and remove the ~ symbol from the name and click yes to confirm changes and restart the xserver. if you can't start x at all use this command ```
sudo nano /etc/X11/xorg.conf~
```press ctrl+o writeout remove the ~ symbol press enter choose yes to save changes then ctrl+x to exit and restart the xserver.

if you have completly hosed your xorg.conf file which i have done a number of times use this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
this will configure the xorg.conf file the way the ubuntu installer did, but by using this you will loose any custom changes you've made to your xorg.conf file like video card driver, resolution changes etc, hope this helps.

---

### Post by Mosey on 2005-12-09
when I do the sudo dpkg-reconfigure it pauses a second then take me quickly to a blue screen that reads

Xserver now disabled. Please restart GDM...or something like that...it's too quick to read really as it quickly disapears and take me back to the white text on black...?

---

### Post by Ocxic on 2005-12-09
Just type

sudo dpkg-reconfigure xserver-xorg

that should work, i dunno what -phigh does and i've never used it??

---

### Post by codejunkie on 2005-12-09
[quote=Mosey]when I do the sudo dpkg-reconfigure it pauses a second then take me quickly to a blue screen that reads

Xserver now disabled. Please restart GDM...or something like that...it's too quick to read really as it quickly disapears and take me back to the white text on black...?[/quote]
try this then press ctrl+alt+F1 this will take you to a terminal mode only then login with your user name and password and then enter this command first
```
sudo /etc/init.d/gdm stop
```
then run 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then
```
sudo /etc/init.d/gdm restart
```
also thought i'd mention that these commands are case sensitive so make sure the caps lock key isn't on and that you don't skip the spaces.

---

### Post by codejunkie on 2005-12-09
[quote=Ocxic]Just type

sudo dpkg-reconfigure xserver-xorg

that should work, i dunno what -phigh does and i've never used it??[/quote]
the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` automatically detects the settings for you just like the ubuntu installer and the live cd do. so if video worked correctly with the live cd or the installer you can run that command to automatically repair your /etc/X11/xorg.conf file.

---

