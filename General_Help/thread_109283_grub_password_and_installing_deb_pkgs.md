---
title: "grub password and installing deb pkgs"
date: 2005-12-28
forum: General Help
---

### Post by blue42 on 2005-12-28
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

I'd like to set up a password for grub and have tried uncommenting the bottom two lines but it didn't work when I tried rebooting. I used the password encryption command to make the md5 sum for my password rather than simply uncommenting the lines

eg
password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
password topsecret

is this not right, does like it says have to be at the beginning of the menu and does the command 'lock' have to be uncommented also?

Not able to find programs through synaptic, I've come across programs I'd like to have installed that can be downloaded as deb packages but can't figure out how to install them I've tried archive manager to open the package but can't figure out how to install them from there. I've tried synaptic to try to find it on my hard drive without any luck.

---

### Post by encoe on 2005-12-28
to install debian packages run in terminal: 

sudo dpkg -i nameofthepackage.dep

---

### Post by blue42 on 2005-12-28
Thanks encoe have gotten use to the graphical interface and although excellent with dos commands it's too easy to be lazy and not get a handle on linux commands.

---

### Post by psusi on 2005-12-28
Why?  If someone really wants to boot up your computer they just have to insert a boot disk and they can bypass your grub password.

---

### Post by blue42 on 2005-12-28
I wasn't aware that posting was an opportunity for others to criticize. If you must know, I didn't bother to make a boot disk and I would like to keep other people off my system.

---

