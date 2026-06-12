---
title: "Grub Loader"
date: 2006-01-12
forum: General Help
---

### Post by noob_Lance on 2006-01-12
Hey,

I was wondering if there was a way to make a "graphical" interface for grub, kind of like the way Ubuntu have there little "graphical" interface for when the system is loading all the modules.

Anyone have any ideas at how to do anything like this???

---

### Post by o_fortuna on 2006-01-13
Unless you were to rewrite the program itself, I don't think you can really have a "GUI" necessarily for GRUB. If you just want pretty colors and a nice background, though, read on.

I always make a splash image for Grub, just cuz I like to. It just has to be a .xpm file in 14 colors and 640x480 resolution in /boot/grub/images. Copy
```
sudo mkdir /boot/grub/images
sudo gedit /boot/grub/menu.lst 
```
into a terminal (Applications-->Accessories) and then delete the line that says "pretty colors" and the line below that, and replace it with this:
```
## Splash Image
splashimage (hdx,x)/boot/grub/images/name_of_image.xpm

## Pretty colors
color yellow/white brown/white 
```
Where x,x is your hard drive (probably 0,0 if only Ubuntu is installed; if you have windows, it's probably 0,1. Look near the bottom of the file where a line starts with "root", which is followed by the right numbers.) and name_of_image.xpm is the name of the image, of course! ;)
Then, put a 14-color .xpm file in the boot/grub/images folder like this (if the image is saved to the Desktop):
```
cd Desktop
sudo cp name_of_image.xpm /boot/grub/images/
```
Now you can restart your computer and see the pretty Grub. :) If the screen goes blank, that means something went wrong (like the image wasn't there), but the default operating system (nearly always Ubuntu) will automatically load in a few seconds.

This is the image I use (just so you don't have to make one yourself, I don't think it's too bad for 14 colors, but I'm not that artistic, so...).

---

### Post by noob_Lance on 2006-01-13
sweet... what resolution (X by Y) does it have to be at in order to be full screen in the grub?

and lol i dont have the skills to re-write it yet lol... but hopefully.. by the time i graduate as a software engineer from here... ill be able to.. or.. if i get bored and deside to do it for fun lol

---

### Post by blackant on 2006-01-20
I couldn't get a full screen picture too. :(
only get a line saying loading...:confused: 

anything wrong somewhere?

---

### Post by veloct on 2006-01-20
There's a program called grubconf which is a graphical interface for managing grub.  I use the command line but you may try it.  I believe you have to have multiverse or universe repo's active to apt-get it.

---

### Post by NESFreak on 2006-03-10
grubconf can be downloaded here (it's marked unstable so you cant download it tru ubuntu but the debian version works for me)
just do "sudo dpkg -i <the_file>.deb" from the commandline
and then run "sudo grubconf" (also in the commandline)

---

### Post by Eddy DaKillaBee on 2006-03-11
Wait... where can I get grubconf? I see "grubconf can be downloaded here" but there's no link... thanks!

---

### Post by Kulkat on 2006-03-11
ubuntu5.10 
Installation was fine but i just could not log in at the logon screen.
As soon as i move the mouse, system freeze or  just reboots to command prompt.


 I have ATI R92LE. If i replace my hard drive with another drive that has Suse 10
 it works fine.
 
 What should i do ?

 Kulkat

---

