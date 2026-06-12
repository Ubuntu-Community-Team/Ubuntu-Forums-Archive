---
title: "Running Loki Patches on AMD64"
date: 2009-01-03
forum: Gaming &amp; Leisure
---

### Post by fuzzykitty on 2009-01-03
At long last I've attempted to restore some of my old Loki game on my new dual core AMD 64 system and have run into trouble.  Just to chronicle what I've done so far, I managed to Heroes of Might and Magic III installed by doing the following:

sudo apt-get install ksh

sudo linux32 ksh setup.sh

Why "ksh" is required and "sh" won't work I have no idea but this made it work based off of some forums.

Now I want to install the patches so my wife and I can play a networked game but I have run up against a brick wall.  Based upon a number of forum posts I have done the following

root@K4:/usr/local/games/Heroes3# export _POSIX2_VERSION=199209

I should add that the loki patch is residing in the program directory, although whether it is or is in my home directory it does not seem to matter.  I get the following when trying three different commands:

root@K4:/usr/local/games/Heroes3# linux32 sh heroes3-1.3.1-x86.run
Verifying archive integrity...OK
Uncompressing Heroes of Might & Magic III for Linux: patch 1.3.1trap: 126: cd /tmp; /bin/rm -rf $tmpdir; exit $res: bad trap

root@K4:/usr/local/games/Heroes3# linux32 ./heroes3-1.3.1-x86.run
Verifying archive integrity...OK
Uncompressing Heroes of Might & Magic III for Linux: patch 1.3.1trap: 126: cd /tmp; /bin/rm -rf $tmpdir; exit $res: bad trap

root@K4:/usr/local/games/Heroes3# linux32 ksh heroes3-1.3.1-x86.run
Verifying archive integrity...OK
Uncompressing Heroes of Might & Magic III for Linux: patch 1.3.1heroes3-1.3.1-x86.run[126]: trap: condition(s) required

Unfortunately I have not been able to find any forum posts with this specific problem nor any related posts with how to fix it (being non root doesn't help either since "export _POSIX2_VERSION=199209" wont work) I've also changed the permissions of the patch to be executable and the Heroes program directory permissions to 0777.

My system is an Intrepid 64bit upgrade of Hardy.  Running AMD X2 5600 and GForce 8600GT.  Any help would be appreciated.  Thanks

Fuzzy

---

### Post by Linux_Gamer_Zinbur on 2009-01-05
Hope you find the answer to your question but I have a problem of my own with Heroes of Might and Magic 3

I type 

sudo apt-get install ksh

 into the terminal window and it works fine I guess don't quite understand all the thing but I generally understood it installed the required program...

But when I type

sudo linux32 ksh setup.sh

or an equivalent i keep getting this message

ksh: line 1: setup: not found

is there some setting I missed?

---

### Post by walter7747 on 2009-01-06
Sorry I havent played that game yet, but i'm a fan.

---

