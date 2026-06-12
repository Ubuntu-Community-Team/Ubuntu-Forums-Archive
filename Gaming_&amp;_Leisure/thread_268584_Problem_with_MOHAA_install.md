---
title: "Problem with MOHAA install"
date: 2006-09-30
forum: Gaming &amp; Leisure
---

### Post by DieselSnorter on 2006-09-30
I'm trying to install MOHAA on Dapper Drake and it's getting stuck asking for the 2nd disc.  I've tried using mohaa-lnx-1.11-beta3.run and using what I think is wine (i just double click the setup.exe on the 1st cd and it goes) and get the same issue.  When I use Wine, I am presented with the option to browse for the CD, so I point it to CDrom0, but it doesn't recognize the disc is there.  

Any ideas? 

Thank you, 
Eric

---

### Post by DieselSnorter on 2006-10-01
no ideas?

---

### Post by traxtar3 on 2007-09-09
I had the same problem. here is what i did...

sudo rm -rf /usr/local/mohaa 
(removes any old install files)

then remove all files in /tmp dir

sudo su
(login as root)

cd /mohaa/.run/location (/home/user_name/Desktop)
./nameofmohaafile.run

if that does not work then try logging in as root then repeat all of the steps

hope this helps

---

### Post by Gordy on 2007-09-09
> **traxtar3 said:**
> I had the same problem. here is what i did...

sudo rm -rf /usr/local/mohaa 
(removes any old install files)

then remove all files in /tmp dir

sudo su
(login as root)

cd /mohaa/.run/location (/home/user_name/Desktop)
./nameofmohaafile.run

if that does not work then try logging in as root then repeat all of the steps

hope this helps


Is this Medal Of Honor and if so , is there a linux version and where can I get it...

---

### Post by traxtar3 on 2007-09-10
it is medal of honor: allied assault
It uses the same disks to install as windows
just get the loki installer for MOHAA 

[http://www.liflg.org/?catid=6&gameid=8](http://www.liflg.org/?catid=6&gameid=8)

get the installer and use it as follows:

cd /to/download/dir

sudo su

./mohaainstaller.run

enjoy

---

### Post by DieselSnorter on 2007-11-17
okay, so a long time later, I was able to get this resolved.  What can I say, I work too much :)
So, it launches now but I had to do some tweaking to get it to work.  The only way it will launch currently is with the following command:
sh mohaa +set r_gldriver libGL.so.1

like I said it works, however, it won't shut down when I close the game.  I usually have to reload Gnome to get out of it.  Ideally, I'd like to it be in its own window so I can minimize or close it when I want to do other things.  

I tried tweaking this setting in my Wine Settings, but no dice. 

I don't have a lot of time for games, but this ones been sitting on my shelf taunting me, and it bugs me when I can't make stuff work (comes with the job I guess). 

As usual, any help you can provide will be greatly appreciated.

---

