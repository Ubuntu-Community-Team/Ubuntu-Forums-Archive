---
title: "Hard Drive full?"
date: 2005-03-06
forum: Desktop Environments
---

### Post by puzzledm on 2005-03-06
I have just been told that my hard drive is full.  This is a bit strange.  I have a 30GB hard drive, in my home directory I have 11Gb and about 7GB spare, which means that Ubuntu is theoretically using up 15GB of space.!

Now this just seems strange has anybody got any ideas how to find out where all the space is being used up and any hints on 'house cleaning' things that I can do to find un-needed usage and stamp it out.  

Help would be much appreciated.

---

### Post by alastair on 2005-03-06
Probably cache - perhaps from packages (apt).

Anyway - check :

sudo du -kx / | sort -n

If it is cached packages, you could use "apt-get" to clean the cache i.e. remove downloaded packages - see "man apt-get".

---

### Post by WW on 2005-03-06
Two useful commands are **df** and **du**.  Try
```
df -h
```to see the sizes and available space of the mounted filesystems.  The command```
du * -s -h
```will the list size of all the files and subdirectories in the current directory.  Take at look at the man pages for more options.


Also, be sure to check for any large log files in the directory /var/log.

---

### Post by bored2k on 2005-03-06
[QUOTE=alastair]Probably cache - perhaps from packages (apt).

Anyway - check :

sudo du -kx / | sort -n

If it is cached packages, you could use "apt-get" to clean the cache i.e. remove downloaded packages - see "man apt-get".[/QUOTE]
 from CACHE ?? What couldva he apt-got ??!?!?! TITANIC: THE SEQUEL DVD??!@??!


lol :P

---

### Post by rosslaird on 2005-03-06
One of the best ways to track down disk usage is with filelight. It shows you graphically what's taking up the space. It's a very cool program.

sudo apt-get install filelight

Ross

---

### Post by WW on 2005-03-06
Ross, thanks for the tip about filelight.  It is pretty cool.

(But it crashed with a SIGSEGV when I made its window a lot larger.  I guess I just won't do that in the future. :)

---

### Post by puzzledm on 2005-03-06
great programme is there something similar for Gnome?

---

### Post by LongTooth on 2005-03-07
Checked out the link on filelight. That does look like a nice program to have. And I too would like to know if there is a gnome version. When 'sudo apt-get install filelight' I couldn't help notice this looks like a program more for KDE. Not that I have anything against KDE. But I'd like to stick to Gnome programs as much as possible. Any one know of something similar for Gnome? Thanks.

---

### Post by bored2k on 2005-03-07
[QUOTE=LongTooth]Checked out the link on filelight. That does look like a nice program to have. And I too would like to know if there is a gnome version. When 'sudo apt-get install filelight' I couldn't help notice this looks like a program more for KDE. Not that I have anything against KDE. But I'd like to stick to Gnome programs as much as possible. Any one know of something similar for Gnome? Thanks.[/QUOTE]
 It is a KDE application. When u installed, u had to download a bunch of _____, including kdelibs .

I like it , but i dont even wanna see anything starting with kde on my box.

---

### Post by v79 on 2005-03-07
I can recommend a little java program called jdiskreport - no KDE dependencies, or Gnome dependencies either. And works equally well in Windows, should you have that need.

LJD

---

### Post by puzzledm on 2005-03-08
I realised what the problem is.  Some of the programmes do read hidden files and others don't.  Nautilus doesn't!  It just means that something was telling me one thing and some the other.  And I didn't realise how much I had in my Point2Play hidden files! 

Oh well problem solved and loads of space now!

Thanks for all your help. =D>

---

