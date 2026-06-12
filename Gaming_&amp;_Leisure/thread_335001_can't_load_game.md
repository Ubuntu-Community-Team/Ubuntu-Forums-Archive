---
title: "can't load game"
date: 2007-01-09
forum: Gaming &amp; Leisure
---

### Post by rgp-02 on 2007-01-09
just loaded ubuntu 1st time. like it so far.  tried to load UT2004 w/no success. no idea how to get install going.......help!

---

### Post by taurus on 2007-01-09
Move to Gaming & Leisure.

---

### Post by Sasa_Ivanovic on 2007-01-09
Is UT2004 Linux version of the game ?

---

### Post by rgp-02 on 2007-01-09
NO!.........thanks for pointing that out!

---

### Post by rgp-02 on 2007-01-10
i inserted the dvd and the file browser opened and there was an option "linux-installer.sh". i tried double clicking it and right clicking it and pushed every button and can't make anything happen.

---

### Post by rgp-02 on 2007-01-10
......as far as a “linux version” of ut2004, i don't believe one exists....and why then 
would they put the little penguin logo on the box for this game?

---

### Post by The Joe on 2007-01-10
Try [Wine]("http://winehq.com") or [Cedega]("http://transgaming.com").

Or in terminal: ```
sh path/to/linux-installer.sh
```

---

### Post by rgp-02 on 2007-01-10
thank you but wine has a directory of text that would take me a month to read through (since i have to work and do other time consuming things that life requires) and don't have an unlimited time resource in which to sit in front of a computer.......cadega wants money..........and

sh path/to/linux-installer.sh   doesn't work either. i get:

rp@rgp-02:~$ sh path/to/linux-installer.sh 
sh: Can't open path/to/linux-installer.sh
rp@rgp-02:~$ 

all i want to do is run a game program....can any one help?
does anyone know how to solve this mystery? or am i beating a dead horse?

---

### Post by M_the_C on 2007-01-10
Insert the disc and wait for it to be mounted. (an icon should appear on the deskto.)

Open a terminal and type:  
```
cd /media/cdrom0
```
assuming the drive you inserted it in is the first drive.

Then type:
```
sh linux-installer.sh
```

The setup program should start, simply go for the defaults.

That should work.

---

