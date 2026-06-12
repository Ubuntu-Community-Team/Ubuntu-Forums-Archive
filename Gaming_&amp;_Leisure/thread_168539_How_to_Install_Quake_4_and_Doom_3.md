---
title: "How to Install Quake 4 and Doom 3???"
date: 2006-04-30
forum: Gaming &amp; Leisure
---

### Post by sardopsycho on 2006-04-30
I am a n00b at installing games and getting them to work on Linux - can anyone help with this???

---

### Post by huckem on 2006-04-30
Quake 4:
[http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

Doom3 is similar, do a google on it and you'll find it.

---

### Post by sardopsycho on 2006-04-30
Ok, I understand the directions, but I am having trouble finding help with creating directories and copying files in Terminal...gotta serach out some info on that.

---

### Post by sardopsycho on 2006-04-30
Ok, I understand the directions, but I am having trouble finding help with creating directories and copying files in Terminal...gotta serach out some info on that.

---

### Post by huckem on 2006-04-30
I found that its best to run the installer first and copy the files into the directory after

---

### Post by sardopsycho on 2006-04-30
Ok...I am actually not clear on these directions.  I have download both RUN files:

doom3-linux-1.3.1302.x86.run
and
quake4-linux-1.2.1.x86.run

But the instructions on the links you sent me do not tell me how to "install" these.  I went ahead and manually created the folders /usr/local/games/doom3/base and /usr/local/games/quake4/q4base.

The instructions really don't say where to go from there.

---

### Post by sardopsycho on 2006-04-30
Strike that....did a chmod +x on each file then did a sudo ./ to install the files.

All good...I hope heh

---

### Post by testbenchdude on 2006-12-08
Here's a quick one: When I double click the Setup file, it gets to the point where I have to put in a serial number. I put in the number on the back of the game manual, and then it says something like "CDkey.dll unable to load". I know it's right, I did it twice and triple checked the second time.

Help please?

---

### Post by testbenchdude on 2006-12-08
Maybe I should explain a little more. I'm hoping the OP got his problem resolved, I know I sort of drug up this thread from the depths of time. :)

I know the ID released a linux installed, but when I go to the site I'm presented with a dizzying array of choices. I know that I have to open one and select "Save As" and then run it, but which one to choose? Should I go for the latest one, or the earliest and how do I patch it once installed? How do I know what version I have (Windows 4 CD pack)?

Here's my progress:

I decided to d/l the latest installer.
Following the directions on [http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

[I]The following files must be copied from the install CDs [1]
to your q4base/ directory ( md5 sums provided as reference ):

If you copy them before running the installer you will need to
create the paths, by default /usr/local/games/quake4/q4base
If you copy after running the installer, make sure not to
replace any paks the installer might have provided.[/I]

I did this:

sudo mkdir /usr/local/games/quake4
sudo mkdir /usr/local/games/quake4/q4base
sudo cp /media/cdrom0/Setup/Data/q4base/game000.pk4 /usr/local/games/quake4/q4base

changed game000.pk4 to the pak and language files stated in the how to, then inserted CD2.

sudo mkdir /home/mikeyc/Desktop/cda
sudo -o norock mount /dev/cdrom /home/mikeyc/Desktop/cda
sudo cp /home/mikeyc/Desktop/cda/Setup/Data/q4base/pak001.pk4 /usr/local/games/quake4/q4base

and so on for the rest of the files (disk2 has pak001-003, disk3 has pak004-006, disk4 has pak007-009).

Now I'm stuck. How do I run the installer? (the .run) file? I put it in the same dir as the files I copied and tried to run it there but no joy.

---

### Post by gnostical on 2006-12-08
> **testbenchdude said:**
> Here's a quick one: When I double click the Setup file, it gets to the point where I have to put in a serial number. I put in the number on the back of the game manual, and then it says something like "CDkey.dll unable to load". I know it's right, I did it twice and triple checked the second time.

Help please?

isnt the serial key on the manuals for a game that plays online usually that is enterted second and the first serial you enter when installing a game is the one on the front of the game cd.

---

### Post by testbenchdude on 2006-12-08
not in this case I think. There is only one serial that I can find.

Back to my question, this is what I get when I double click the .run file:

Could not open the file /usr/local/games/quake4/&#8230;uake4-linux-1.0.6.x86.run.

EDIT*

NM I got it to work! This is something I did not know, but after searching around for about 20 minutes I discovered that I have to type "sh" in order to run that .run file.

WOOT it works! My first Linux game. FRAG ON!!!

---

### Post by luvinit on 2006-12-10
I see you managed to get hold of the linux installer ok. I personally had problems getting hold of quake 4, so I made a torrent for it which might be useful for anyone in the future

[http://www.torrentportal.com/details/826542/quake4-linux-1.3-2.x86.run.html](http://www.torrentportal.com/details/826542/quake4-linux-1.3-2.x86.run.html)

---

### Post by Raklau on 2007-09-14
Hello, sorry for dragging this post back up but I'm a new user with Ubuntu Linux 7.04 and I 'm havening problems installing the quake4-linux-1.4.2 x86.run file I downloaded following what has been said in the post's, I've tried running it in the terminal and get an access denied message ,this is what I'm doing

I open the terminal 

raklau@raklau-desktop:~$

and type sh and then the path

$ /home/raklau/desktop/quake4-linux-1.4.2.x86.run

and this is what it says

sh: /home/raklau/Desktop/quake4-linux-1.4.2.x86.run: Permission denied
or
sh: /home/raklau/desktop/quake4-linux-1.4.2.x86.run: not found

I'm not sure what I'm doing wrong but this is getting frustrating,I've tryed to install it via the Terminal,Add/Remove and Synaptic Package Manager with no luck in fact I've had problems installing stuff like this from day one can some one please help me.

---

### Post by Sockerdrickan on 2007-09-14
set permissions :D

---

### Post by Raklau on 2007-09-14
aahh nvm, I found I had to type in sudo sh to install

---

### Post by Sockerdrickan on 2007-09-14
Yep that's how to do it if you are in a terminal already and want to install as root!

---

### Post by naifnezar on 2009-07-14
hi... after 2 years. hope can get some answer. anybody still have the installer? i cant seem to download the installer. i just realize i do need at least one game or two in my ubuntu.
help needed.

---

### Post by Brebs on 2009-07-14
Here's my [Quake 4 DVD installer script](http://www.fedoraforum.org/forum/showthread.php?t=189064).

---

