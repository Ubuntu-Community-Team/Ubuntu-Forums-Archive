---
title: "Unreal Tournament 2004 Cache Problem"
date: 2005-05-16
forum: Gaming &amp; Leisure
---

### Post by Jan_DarK on 2005-05-16
Hi all :)
I recently moved from Windows to Ubuntu and i am xtremly happy for it :) Everything works fine except some things...
As a fanatic of UT2004, the first thing I did after Ubuntu install and configuration completed, I tried to install UT2004.

The installation was successfull. The frame rate was from 40-50% higher that windows!!! I could believe in my eyes. The problem came up when I tried to play online.

UT as always started to download safegame, utcomp etc.... But when those packages rechees 100% it pop ups a message that tells me: Failed to download package: "utcomp" or "safegame" or or... Server Refused to send...

I copied from the windows installation the cache and everything is just fine. But whenever I find a server with something that I don't have there is a problem :S

OS: Ubuntu 5.04 AMD64-bit edition
H/W: 
AMD 64 3000+
M/B MSI MicroATX
512MB Ram
Ge-Force Ti4800 128MB
SoundBlaster 5.1 Live

The install of UT2004 was made by root:
sudo installer.sh (i don't remember the exact name of the installer (I am not at my PC right now))
the game was installed in the following path: /usr/local/games/UT2004/
and in the home directory of my account (jandark) are those folders with files inside:
/home/jandark/.ut2004/Cache/
/home/jandark/.ut2004/System/

The game works just fine and the only problem is the cache :( You can understand how annoying this is right? :)
(I am the root of this system of course)

Anyway except from this problem I would like to give a BIIIIIIG THANKS to this community for the great job that they have donne. I hope to help anyone I can here.

Since that this is my first post and my English are crappy :P be gentle with me :)

---

### Post by jdodson on 2005-05-16
did you patch the game to the latest version?

---

### Post by Jan_DarK on 2005-05-17
[QUOTE=jdodson]did you patch the game to the latest version?[/QUOTE]
 Yes I have installed ece bonus pack, patch 3355 and CBP2 vol1 and vol2 :)

---

### Post by robtotheb on 2005-05-21
Did you find a solution to this problem?  The games runs great but querying the server fails

---

### Post by Jan_DarK on 2005-05-21
[QUOTE=robtotheb]Did you find a solution to this problem?  The games runs great but querying the server fails[/QUOTE]

no man :)
unfortunatly I haven't. do you have the same problem ah?

I can play online if i put in the Cache folder the same cache files from a windows installation. Try that. Ask the files from a friend or something.

By the way... My problem is not the querying on the master server or during the connect to a server. The problem is that UT is downloading the packages until 100% and then says refused to send. It is like i don't have permission to write in the cache folder although I run it as root.

---

### Post by robtotheb on 2005-05-22
mine just doesnt find the servers... could u email me ur cache folder?

---

### Post by apollyonis on 2005-05-22
Could you go to terminal and find out what the file permissions are?

```
cd /home/jandark/.ut2004/Cache/

ls-lg

```
```
cd /home/jandark/.ut2004/System/

ls-lg
```

Find out what the file permissions are set to. You could probably do : 

```
sudo chmod -R a+rwx /home/jandark/.ut2004/Cache /home/jandark/.ut2004/System 
```

From both directories to give permission to read, write and execute files for both directories for the owner,group and others just in case. Personally I wouldn't see that as much of a security breach since its just game files you're altering.

Edited

---

### Post by robtotheb on 2005-05-28
Changed the permissions to my user name and it works online now :)

Thanks

---

