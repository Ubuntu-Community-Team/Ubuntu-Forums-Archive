---
title: "unFormat? Recovering what is lost"
date: 2009-01-01
forum: General Help
---

### Post by lordtetris on 2009-01-01
Hallo!

The short story:

Is there native programs for Ubuntu that can recover a formated disk.
(Even if its was a windows ntfs system installed on the drive?)

The more ditailed:

I decided to get linux 2 month's ago and from the first time i used it i loved it. 
But still i work whit game making and photoshop and 3dsmax where hard to get to work well in wine. 
So i have had both my computers duel-booting. Having one hard drive for linux and one for windows all works fine.
One day only slept 3 houers deciding i whant to format my USB-stick.
Gparted used tired and stupid not formatting my USB-stick but my other hardrive. (Yes I'm a stupid **** i know :P ) Alot of work gone and now i wonder do i relly ahve to uninstall Ubuntu install Xp try using one of those Recovery programs. THen re installing ubuntu. Ore is there a way to do it in ubuntu? 

(and no wine and emulation of xp using windows recovery programs did not work yet. think it has somthing to do whit the MBR)

Would be relly pleased if somone could help thanx on forehand!
(Sorry for the bad spelling)

---

### Post by logos34 on 2009-01-02
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

sudo apt-get install testdisk

sudo testdisk

---

### Post by hyper_ch on 2009-01-02
what is also recommended is:

(1) to buy a second drive that's at least equal in size
(2) boot a live linux session
(3) mirror the formatted drive to the new one with the dd command so you get a 1:1 copy

That way you can work on the mirror and try to recover stuff there and it won't degrade data any further.

---

### Post by lordtetris on 2009-01-02
Thanx alot for the help! :D

---

### Post by lordtetris on 2009-01-02
First I really want to say thanks alot! For the help I got allot of files back.
And It really saved my skin.

But I have another question still. 
After recovery all files are locked and when i try to open they say permission denied they are not yours.

I found on the web that i could write: 

   sudo chown user:user /dir

But it only gets me in to one folder at the time, 
and all the files inside are locked.
Is there any way to add somthing to the command line so that all files and folders that are inside the folder are also converted to being my property?

(And a little extra question if I whant to lern more about the terminal is there any good place where commands are listed ore a guide?)

Thx for the help!

---

### Post by logos34 on 2009-01-02
'recursive' option:

sudo chown **-R** user:user /mount/point

---

### Post by lordtetris on 2009-01-02
Thx !

---

