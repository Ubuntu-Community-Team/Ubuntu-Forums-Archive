---
title: "need some basic help on user info"
date: 2005-07-01
forum: Desktop Environments
---

### Post by scottmcf on 2005-07-01
I'm new to both linux and ubuntu and have already solved some problems with my recent installation:  Toshiba satellite 4090DVD laptop.   

However, I want to get my DVD player to play DVDs and have read some online help stuff that tells me to install and run Regionset.  This is where my questions begin.  I can seem to install programs as I'm not the root user and I have permission troubles.  How do I log on as the root user?  I only chose one user password and name during installation. :-? 

Cheers,

---

### Post by Lunde on 2005-07-01
[QUOTE=scottmcf]I'm new to both linux and ubuntu and have already solved some problems with my recent installation:  Toshiba satellite 4090DVD laptop.   

However, I want to get my DVD player to play DVDs and have read some online help stuff that tells me to install and run Regionset.  This is where my questions begin.  I can seem to install programs as I'm not the root user and I have permission troubles.  How do I log on as the root user?  I only chose one user password and name during installation. :-? 

Cheers,[/QUOTE]
 use the sudo command. Exs:
$ sudo apt-get install packet_name

---

### Post by Lunde on 2005-07-01
Before you do the region set, see if this works 
$ sudo apt-get install libdvdcss2

---

### Post by scottmcf on 2005-07-01
I'm going to try this out tonight.

Cheers,

---

### Post by scottmcf on 2005-07-01
[QUOTE=Lunde]Before you do the region set, see if this works 
$ sudo apt-get install libdvdcss2[/QUOTE]
 If I want to do this from the GUI, is it possible to log on as "owner" or "root"?

---

### Post by Lunde on 2005-07-01
[QUOTE=scottmcf]If I want to do this from the GUI, is it possible to log on as "owner" or "root"?[/QUOTE]
 Try 
$ sudo -s

Another way more permenent:

$ sudo xterm
$ passwd

enter root password

---

