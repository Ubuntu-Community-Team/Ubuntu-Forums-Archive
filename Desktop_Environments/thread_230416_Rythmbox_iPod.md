---
title: "Rythmbox iPod"
date: 2006-08-05
forum: Desktop Environments
---

### Post by Sethro on 2006-08-05
I tried everyhthing, GTKPod and Banshee. I am trying to copy music from my ubuntu 6.06 box over to my 20GB iPod. 

So far I have tried :

-Formatting
-Re-Writing all music

Rythmbox is able to find all my music already on my iPod, it can even play it too. But I cant seem to transfer music.

Weird thing is the iPod shows up on my desktop, which means its already mounted right..


Any help guys?

---

### Post by Jagot on 2006-08-05
I could be wrong but I'm not sure that Rhythmbox can.  You may want to read this:

[https://help.ubuntu.com/community/IPodHowto](https://help.ubuntu.com/community/IPodHowto)

---

### Post by Sethro on 2006-08-05
yeah i see.


I already have alot of music on my iPod which i want to keep, what do you suggest?

---

### Post by Jagot on 2006-08-05
I would suggest you try gtkpod again, ensuring you download the gtkpod-aac package.

---

### Post by Sethro on 2006-08-05
Getting the following error messages :

Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.

---

### Post by Sethro on 2006-08-05
And when I close GTKPOD I get this error :

Unmounting of '/media/ipod' (/dev/sda2) unsuccessful.

---

### Post by Sethro on 2006-08-05
And this when i try again :

'/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted.

---

### Post by Sethro on 2006-08-05
Jagot u still there buddy?

---

### Post by hotani on 2006-08-06
you have to first create the ipod directories if you can. Go to file -> 'create ipod directories' from gtkpod. Once you drag your stuff over, you have to 'sycronize itunes DB' for the changes to stick. It's a lot of extra steps and not very intuitive but until we get iTunes on Linux I guess this is the only option. :(

Last time i tried it the ipod got stuck mounted with the firewire. I ended up rebooting and using USB, then it seemed fine.

---

### Post by Sethro on 2006-08-06
Thanx hotani ur the man of the hour.. lol

got it working finally after 4 hours! lol

Anyways YEAH why the fudge wont apple make itunes for linux. I mean it would get rid of some many problems. Alot of people would switch to linux...

---

