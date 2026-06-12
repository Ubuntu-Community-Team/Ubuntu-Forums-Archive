---
title: "Opening .Bin files"
date: 2009-01-22
forum: General Help
---

### Post by MikeylovesJade on 2009-01-22
Well im having trouble opening .bin files, i try just opening them and it wants another application to open them with, is there something i need to download to open them with?

And i tried using the terminal with chmod 755 aim.bin but it doesnt work, i tried Sudo chmod +x aim.bin and then it asks for a password which i figure it might just be my admin pw, so i put it in and it says file not found, i have it on the desktop but is there a command line to put in the terminal to where i can show its on the desktop n open it?

sorry if this is the wrong spot to post this, wasnt sure where to post this one at n im brand new to ubuntu. any help i would greatly appreciate. (btw have the newest version.)

---

### Post by sedawk on 2009-01-22
If you can see aim.bin on your Desktop you first have to go to
the correct directory after opening a terminal:
```

cd ./Desktop
chmod u+x aim.bin
# before doing this read below !
./aim.bin

```
You can check with "file" what is inside "aim.bin" - if it is really
an executable or something else:
```

cd ./Desktop
file aim.bin

```

---

### Post by Lod on 2009-01-22
In the terminal either try sudo chmod +x Desktop/aim.bin

or do
cd Desktop
sudo chmod +x aim.bin

Afterward you should be able to run it wit ./aim.bin in the terminal (or doubleclick on the desktop).

---

### Post by MikeylovesJade on 2009-01-22
heres what my terminal says :/ n its on the desktop..


open@terminator:~$ sudo chmod +x Desktop/aim.bin
chmod: cannot access `Desktop/aim.bin': No such file or directory
open@terminator:~$ sudo chmod +x Desktop/yohoho-install.bin
open@terminator:~$ cd ./Desktop
open@terminator:~/Desktop$ ch mod u+x yohoho-install.bin
bash: ch: command not found
open@terminator:~/Desktop$ chmod u+x yohoho-install.bin
open@terminator:~/Desktop$ sudo chmod u+x yohoho-install.bin
open@terminator:~/Desktop$ sudo chmod +x aim.bin
chmod: cannot access `aim.bin': No such file or directory
open@terminator:~/Desktop$



edit: well i got the puzzle pirates to work by putting /home/open/desktop/yohoho-install.bin but i tried the same with aim and it wouldnt work :/

---

### Post by MikeylovesJade on 2009-01-22
sry for double posting but now it tells me permission denied, anyone know where under authorizations i need to go to? :(

---

### Post by mister_pink on 2009-01-22
do 

```

cd Desktop
ls -l

```
Copy and paste to make sure its right (its ctrl shift v to paste in a terminal), then post the relavent lines (or all if you want) here so we can see what the permissions are at the moment.

---

### Post by Lod on 2009-01-22
Although it looks like you don't have a aim.bin file...

---

### Post by MikeylovesJade on 2009-01-22
k here it is, sry guys but i appreciate u helping me, its sooooo much different then windows xp :(


open@terminator:~$ cd Desktop
open@terminator:~/Desktop$ ls -l
total 470944
-rwxr-xr-x 1 open open     39052 2003-01-10 09:37 aim
-r-------- 1 open open   1118089 2009-01-22 06:51 aim-1.5.286.tgz
drwxr-xr-x 2 open open      4096 2009-01-22 07:02 bin
-rw-r--r-- 1 open open      5621 2008-10-31 10:43 gnome-appearance-properties.desktop
-rw-r--r-- 1 open open  19565413 2009-01-22 09:41 jre-6u11-linux-i586-rpm.bin
-rw-r--r-- 1 open open      1921 2008-09-26 15:25 launch
drwxr-xr-x 3 open open      4096 2003-01-10 10:16 lib
-rw-r--r-- 1 open open   8398610 2009-01-22 09:36 pidgin-2.5.4.tar.bz2
-rw-r--r-- 1 open open 449197354 2009-01-22 05:45 RegnumOnlineInstall_32
-rw-r--r-- 1 open open   1857900 2009-01-21 15:38 swflash.cab
drwxr-xr-x 2 open open      4096 2009-01-22 07:01 usr
-rw-r--r-- 1 open open    763963 2009-01-22 07:16 yohoho-install(2).bin
-rwxr-xr-x 1 open open    763963 2009-01-22 07:13 yohoho-install.bin
-rw-r--r-- 1 open open       184 2009-01-22 09:54 Yohoho! Puzzle Pirates.desktop
open@terminator:~/Desktop$


And there is a .bin file of aim too cause i downloaded it. n as u can see i even tried pidgin but then it says permission denied when trying to open n when i try opening yohoho puzzle pirates.desktop it wont it gives me more errors.

open@terminator:~/Desktop$ /home/open/Desktop/Yohoho! Puzzle Pirates.desktop
bash: /home/open/Desktop/Yohoho!: No such file or directory
open@terminator:~/Desktop$

---

### Post by Lod on 2009-01-22
All right, I've never realized aim the aim messenger. You can use Pidgin for this (as you already discovered). Luckily pidgin is installed by default with your Ubuntu installation. Go to Applications - Internet - Pidgin.
I'm not sure how much you know already about Linux so I'm trying to be a as simple as can be. Maybe unnecessary but there you have it.

First of all, if you need software in Ubuntu (or Linux) the first place you have to look is Applications - Add /Remove... or System - Administration - Synaptic Package Manager. Over 18.000 software packages have been made available for Ubuntu. Just search, click and install. You rarely have to install something more difficult.

Back to your listing. 
The first file is aim, without the .bin part. Probably this was lost somewhere during the saving actions. You don't need the bin part however, It is already executable (the rwx r-x r-x in front of the file indicates the file permissions, the names after it (in your case open open) are the user group who owns the file. You can either have Read, Write and eXecutable. The first 3 characters point to the user, the second to the group and the third to the rest. If there is a d as first character it means it is a directory.

You can delete (you should delete) everything but the aim and the yohoho-install.bin files. You don't need the aim at all because you have pidgin.
Double click on yohoho-install.bin and it should install, not unpack the files. You can do it from the terminal as well by going to your Desktop (cd Desktop) and type
sudo ./yohoho-install.bin

Hopy it works.

edit:
Desktop files by the way are not supposed to be on the Desktop. They define the entry of a program in the menus. The installation process will place them in the correct location.

---

### Post by oldos2er on 2009-01-22
"k here it is, sry guys but i appreciate u helping me, its sooooo much different then windows xp :sad:"

 You're making it needlessly complicated. Let one of the package managers install aim (or anything else). Please read [https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)
and [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by MikeylovesJade on 2009-01-22
far as the yohoho-install.bin file goes, i got it to install n it shows the icon on the desktop but when i click it nothing happens and when i use the terminal to open it it says permission denied and it is compatable with linux i checked. :/



edit: Also under the add/remove programs its not there under 3rd party or anything yet it is installed.


open@terminator:~/Desktop$ ls -l
total 21176
-rw-r--r-- 1 open open     5621 2008-10-31 10:43 gnome-appearance-properties.desktop
-rw-r--r-- 1 open open 20106959 2009-01-22 10:10 jre-6u11-linux-i586.bin
-rw-r--r-- 1 open open   763963 2009-01-22 07:16 yohoho-install(2).bin
-rwxr-xr-x 1 open open   763963 2009-01-22 07:13 yohoho-install.bin
-rw-r--r-- 1 open open      211 2009-01-22 11:10 Yohoho! Puzzle Pirates.desktop
open@terminator:~/Desktop$

---

