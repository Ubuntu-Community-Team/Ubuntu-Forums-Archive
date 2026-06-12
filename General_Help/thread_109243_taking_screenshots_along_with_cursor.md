---
title: "taking screenshots along with cursor"
date: 2005-12-28
forum: General Help
---

### Post by h4lfl1ng on 2005-12-28
is this possible? Or does anyone have the 5.10 images of the default coursors. Or can anyone help me compile gcursor with mono..im confused on that part..

oh wait, i remember theres a terminal command for taking SS's, but what is it and does it take ss's of cursors too?

and the gimp screenshot tool dont take pics of cursor, lemme try xwd command, nope that requires mouse, which changes to a '+' to take ss..

---

### Post by Pablo_Escobar on 2005-12-28
The command is **scrot**, but You'll need to apt-get it :)
I don't know if it'll catch the cursors, worth to try.

---

### Post by anil_robo on 2005-12-28
command for screenshots:
```
gnome-screenshot
``` Help manual for this command
```
gnome-screenshot --help
```

---

### Post by h4lfl1ng on 2005-12-28
Well scrot isnt in the default apt-get rep, and gnome-screenshot is just the regular screenshot app that doesent take pics of cursors.. and theres nothing bout cursors, and man doesent have any info on it either. Thanks anyways for the fast replies.

---

### Post by Pablo_Escobar on 2005-12-28
scrot is in the universe, You just need to uncomment the universe line in /etc/apt/sources.list and You're good to go :)

---

### Post by h4lfl1ng on 2005-12-28
Okay, found the file, and the two lines..now this might be a stupid question, but how can i login as root to edit that file, cuz its chmoded so its uneditable.. When i try login as root it says administrator cannot login here. as in the main login screen.

---

### Post by Pablo_Escobar on 2005-12-28
sudo gedit /etc/apt/sources.list

use sudo before a command for root powers :)

---

### Post by h4lfl1ng on 2005-12-28
Oh, okay gedit was the command..i know bout sudo..heh but didnt know bout gedit

edit:

ilya@irad:~$ sudo apt-get install scrot
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package scrot
ilya@irad:~$

---

### Post by Pablo_Escobar on 2005-12-28
firstly run 
sudo apt-get update
then 
sudo apt-get install scrot

:)

---

### Post by h4lfl1ng on 2005-12-28
OH, so it updates the universal?

Yeh, im kinda new to linux, and ubuntu even more..i used centOS... i love that distro.


um, not cursor, and not parameters to enable it.. damn..now i need a new way.

---

### Post by Pablo_Escobar on 2005-12-28
It updates Your apt cache with information from universe, wich You had disabled before.

---

### Post by h4lfl1ng on 2005-12-28
well scrot doesnt take ss's with cursors.. and nothing about it in 'man scrot' nor '--help'

---

### Post by h4lfl1ng on 2005-12-28
Would anyone happen to have a pic of the default loading cursor and loading cursor-pointer ... or maybe another way to take screenshots with the cursor included? Anyone, plz. Thanks a bunch, this forum rocks. And so des ubuntu. ^^

---

### Post by anil_robo on 2005-12-28
Do a file search for "arrow" with gnome-search-tool ( Menu : Places--> Search for files).
Also, you could get loads of cursors at [www.gnome-look.org]("http://www.gnome-look.org") !
Open your screenshot in GIMP and paste your cursor there! :D

---

### Post by cylon359 on 2005-12-28
xwd can run without the mouse if you give it the window id (found by xwininfo), but unfortunately that still won't capture the mouse cursor since it's a hardware mouse cursor.

There may be an xorg configuration option that uses a software mouse cursor, but I am not sure.  That might work...

---

### Post by h4lfl1ng on 2005-12-28
[QUOTE=anil_robo]Do a file search for "arrow" with gnome-search-tool ( Menu : Places--> Search for files).
Also, you could get loads of cursors at [www.gnome-look.org](www.gnome-look.org) !
Open your screenshot in GIMP and past your cursor there! :D[/QUOTE]


Well i found the cursor files, but what do i open them with? Their sum unknown format.

Yeh gnome-look is a good site, but that cursor theme isnt there .. :(

---

### Post by anil_robo on 2005-12-29
[quote=h4lfl1ng]Well i found the cursor files, but what do i open them with? Their sum unknown format.

Yeh gnome-look is a good site, but that cursor theme isnt there .. :([/quote] 
So sorry to hear that. I thought it over, and here's another trick (and this time I'm sure it'll work).
First, install the gcursor mouse pointer selector by this command:
```
sudo apt-get install gcursor
``` Gcursor will be installed, and you can run it by typing gcursor in the terminal, or ghrough System--> Preferences--> Cursor selection.
WHen you run gcursor, it'll show you all the cursors installed, and you can select from them. Take screenshots of gcursor window (using Alt+Print Screen keys), and retouch it in GIMP to show only the pointer. Here is what gcursor looks like (and be happy - you'll be able to see mouse cursors as graphics): Click the thumbnail to enlarge:
[ATTACH]4902[/ATTACH]

---

### Post by h4lfl1ng on 2005-12-30
Wicked, i tried installing gcursor, but at the time i didnt have universal rep enabled so it didnt work. It has the cursor i need, but it still doesent have all the cursors in the paticular theme... :( There has to be another way. But thanks a bunch, i did get the one i need. It was the circle loading one, the one in ur screenshot.

---

