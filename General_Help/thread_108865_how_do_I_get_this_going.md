---
title: "how do I get this going?"
date: 2005-12-27
forum: General Help
---

### Post by nu2this on 2005-12-27
First I want to get Firefox 1.5 now I've read this  [http://www.ubuntuforums.org/showthread.php?t=75817&highlight=mozilla-mplayer+install](http://www.ubuntuforums.org/showthread.php?t=75817&highlight=mozilla-mplayer+install)
my question is how do i get this ```
deb http://si.archive.ubuntu.com/ubuntu breezy multiverse               
```                                                                                         
into the /etc/apt/sources.list  ? As i read it Ineed to get this for mplayer for videos to play in Fx.
I tried the terminal by entering  /etc/apt/sources.list that got me Permission Denied.
I tried sudo   /etc/apt/sources.list  I then got Password. I entered the password I gave myself at install & got Sorry try again. What password does it want? that's the only one I've got! Also I made 3 attempts & got sorry 3 tries. A 4th attempt was made & it just came back command not found. What does that mean?
Sorry I sound so dumb ,but that's how new I am.

---

### Post by codejunkie on 2005-12-27
[QUOTE=nu2this]First I want to get Firefox 1.5 now I've read this  [http://www.ubuntuforums.org/showthread.php?t=75817&highlight=mozilla-mplayer+install](http://www.ubuntuforums.org/showthread.php?t=75817&highlight=mozilla-mplayer+install)
my question is how do i get this ```
deb http://si.archive.ubuntu.com/ubuntu breezy multiverse               
```                                                                                         
into the /etc/apt/sources.list  ? As i read it Ineed to get this for mplayer for videos to play in Fx.
I tried the terminal by entering  /etc/apt/sources.list that got me Permission Denied.
I tried sudo   /etc/apt/sources.list  I then got Password. I entered the password I gave myself at install & got Sorry try again. What password does it want? that's the only one I've got! Also I made 3 attempts & got sorry 3 tries. A 4th attempt was made & it just came back command not found. What does that mean?
Sorry I sound so dumb ,but that's how new I am.[/QUOTE]
if your using gnome
```
sudo gedit /etc/apt/sources.list
```
if your using kde try either
```
sudo kate /etc/apt/sources.list
```
or
```
sudo kwrite /etc/apt/sources.list
```
add the line to the file save and exit and the run
```
sudo apt-get update
```
before installing new packages.

---

### Post by kosmic on 2005-12-27
in a terminal do :
 
sudo gedit /etc/apt/sources.lst
 
and put that line and save :)
 
 
EDIT :[codejunkie]("http://www.ubuntuforums.org/member.php?u=13310") was fastest :)

---

### Post by odin on 2005-12-27
you have to edit that file:

sudo gedit /etc/apt/sources.lst

I dont know if that line is there and you just need to uncomment it (removing the #) or you have to type it yourself.Save and close the file then type in a terminal:

sudo apt-get update

and after that

sudo apt-get install whatever_you_wanna_install

And the password you have to type when you use sudo is your user's password.

hope this solves your problem

Edit:I can see I'm really slow....

---

