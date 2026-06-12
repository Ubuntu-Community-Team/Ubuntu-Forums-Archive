---
title: "I think I deleted windows"
date: 2009-06-04
forum: General Help
---

### Post by Harry2 on 2009-06-04
well, I reinstalled ubuntu and now windows has dissapeared....

I LOST ALL THE FAMILY PHOTOS AND SOMTHING MY DAD HAS BEEN WORKING ON FOR OVER 6 MONTHS...

I CANT EVEN FIND C DRIVE, COULD IT POSSIBLY BE UNMOUNTED?

---

### Post by Harry2 on 2009-06-04
Sorry for the rage btw, If I dont fix this then I am dead....

---

### Post by Dustin2128 on 2009-06-04
when you boot, what does grub show? could I get exactly what it says?
also, do you have another computer?

---

### Post by freakyruft on 2009-06-04
what option have you chosen in the ubuntu setup when it came to partitioning your hard drive?
is the partition still available?
What does
```
sudo fdisk -l
```
say?

---

### Post by MasterNetra on 2009-06-04
If during Ubuntu's setup you selected the "entire disk" option when dealing with the partition and etc. Then sorry to say your probably dead. Otherwise yea tell us what your options are at boot? (Keep a eye on your screen as your computer is booting up from the off position as it gives you only seconds to select either a Ubuntu option or Windows, otherwise Ubuntu is the default option.)

---

### Post by cybrsaylr on 2009-06-04
Welcome to the club.
Dual booting can be tricky, you have to study it well and know what you are doing.
That said I did the same thing years ago, wiped out windows.
Luckily though, anything important was on an external HDD.
Still it was a pain having to reinstall XP.

---

### Post by pro003 on 2009-06-04
What option did you select when you installed ubuntu when the partitioner asked you? There is Take whole drive, then Resize Windows partition and there is also the best option ==> MANUALLY.

Now, if you selected 'take the whole drive' which is the first option, I suppose you ARE A DEAD MAN. 

Now the only thing that could save you is trying to recover deleted files i.e deleted after accidental formatting of drive.

The best known software for windows is Get Data Back v3.x.x, and there are also linux tools for recovering deleted files, and also live cd's containing various tools for recovering, you could look up for Vortex live cd...

Else, I don't know what to tell you, except I feel sorry for you. 

Hopefully your dad is not some jerk to kill you for this, although it depends what kind of project he's been working on.

---

### Post by Dustin2128 on 2009-06-04
ok, try this if you are versed in cracking the case on your computer (and you have another computer) open up the computer, find the hard drive that you use, and remove it. Plug it in to another computer (not a laptop, a desktop) and boot it up. Make sure the pins are set to slave. When you boot up, if it's a windows rig, you should be able to acess the part of the drive that has an NTFS/FAT partition. if you can't, chances are that the whole drive is ext3, and you are screwed. MAKE SURE THE DRIVE IS SET TO SLAVE

---

### Post by freakyruft on 2009-06-04
why that complicated?
open a terminal, type
```

sudo fdisk -l

```
and you'll know if you are dead. if your win partitions are listed there, you got lucky this time...

---

### Post by hyperdude111 on 2009-06-04
There are some tools that allow you to recover deleted partitions.

---

### Post by Dustin2128 on 2009-06-04
> **hyperdude111 said:**
> There are some tools that allow you to recover deleted partitions.

what, no names?

---

### Post by albinootje on 2009-06-04
> **Harry2 said:**
> well, I reinstalled ubuntu and now windows has dissapeared....

I LOST ALL THE FAMILY PHOTOS AND SOMTHING MY DAD HAS BEEN WORKING ON FOR OVER 6 MONTHS...


- Always make regular backups on external media
- Make backups when re-partitioning or re-installing

- Try testdisk to get your data back :

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Harry2 on 2009-06-04
Thanks for all of the responces!!

Opened terminal, typed;

> sudo fdisk -lThis came up,
[1) http://i41.tinypic.com/15hkhap.png]("http://i41.tinypic.com/15hkhap.png")

2) I didnt use the overwrite windows or expand windows partition, I did it manually.

3) I get these;

ubuntu
ubuntu (recovery)
ubuntu - minidk or somthing
[U]OTHER;
[/U] xp loader


I tried the xp loader thing (got the name wrong) and it just boots up to a blank, blue screen.

4) I didnt have the space to backup ><

5) Thank god all I lost (or maybe not :P)  was DRIVE C, Windows + other files...
    I still have my dads stuff and photos so now all he will kill me for is not having windows



Thanks again

---

### Post by Dustin2128 on 2009-06-04
> **Harry2 said:**
> Thanks for all of the responces!!

Opened terminal, typed;

This came up,
[1) http://i41.tinypic.com/15hkhap.png]("http://i41.tinypic.com/15hkhap.png")

2) I didnt use the overwrite windows or expand windows partition, I did it manually.

3) I get these;

ubuntu
ubuntu (recovery)
ubuntu - minidk or somthing
[U]OTHER;
[/U] xp loader


I tried the xp loader thing (got the name wrong) and it just boots up to a blank, blue screen.

4) I didnt have the space to backup ><

5) Thank god all I lost (or maybe not :P)  was DRIVE C, Windows + other files...
    I still have my dads stuff and photos so now all he will kill me for is not having windows



Thanks again
just remember, always make backups of important files like family photos and projects.

---

### Post by freakyruft on 2009-06-04
congratulations! sure win is lost? or is just the grup-entry missing?

---

### Post by albinootje on 2009-06-04
> **Harry2 said:**
> 
2) I didnt use the overwrite windows or expand windows partition

So you apparently still have the files.. did you check it by mounting the MS-Windows partitions while in Ubuntu ?

And if XP boots into a blue screen, then it sounds like .. a nice question for MS-Windows experts ;-)

---

### Post by Harry2 on 2009-06-04
> **albinootje said:**
> So you apparently still have the files.. did you check it by mounting the MS-Windows partitions while in Ubuntu ?

And if XP boots into a blue screen, then it sounds like .. a nice question for MS-Windows experts ;-)

I dont have the windows files unless its on the drive which is wiped or un-mounted ^^

How do I mount it, its not in the places area...

>                                                    congratulations! sure win is lost? or is just the grup-entry missing?
Its definatly missing in the grup
Its a lose situation but it just got a little bit better :P


EDIT:::

I just checked by right clicking each partition in Gpart and it only says unmount so they are all mounted :(

(btw, If I unmount one, will it remount if I go onto places, [insert folder here])?

---

### Post by Tholley on 2009-06-04
When you partitioned your drive and re-installed Ubuntu, did it ask you which files you wanted to import? If so, then all your files should be there and even the Windows in another partition. If it didn't ask you to import documents and files, then.... oopsie.

---

### Post by Harry2 on 2009-06-04
> **Tholley said:**
> When you partitioned your drive and re-installed Ubuntu, did it ask you which files you wanted to import? If so, then all your files should be there and even the Windows in another partition. If it didn't ask you to import documents and files, then.... oopsie.

It didnt ask me to import things, My other ubuntu is broken...

(See Thread [http://ubuntuforums.org/showthread.php?t=1177820](http://ubuntuforums.org/showthread.php?t=1177820))

---

### Post by albinootje on 2009-06-04
> **Harry2 said:**
> 
How do I mount it, its not in the places area...


```

sudo mkdir /media/sda2
sudo mkdir /media/sda3
sudo mount /dev/sda2 /media/sda2
sudo mount /dev/sda3 /media/sda3

```

Please report back if this gives any errors or problems.

---

### Post by Harry2 on 2009-06-04
> **albinootje said:**
> ```

sudo mkdir /media/sda2
sudo mkdir /media/sda3
sudo mount /dev/sda2 /media/sda2
sudo mount /dev/sda3 /media/sda3

```Please report back if this gives any errors or problems.

I made the folders successfully but...

sda2 is empty
sda3 is just D drive (already accesible)


Should I do the same operation for sda1 and sda4?

---

### Post by albinootje on 2009-06-04
> **Harry2 said:**
> I made the folders successfully but...

sda2 is empty
sda3 is just D drive (already accesible)


Should I do the same operation for sda1 and sda4?

No. sda1 looks like the MS-Windows recovery partition, and sda4 looks like your Ubuntu partition.

I suggest to use testdisk from a "live session" from an Ubuntu installation cdrom or usb stick.

And make backups from what you still have to external media first, in case you didn't do that.

Also.. for recovery of data it is important to not use the hard disk for too long, for writing/renaming/moving files.

Good luck!

---

### Post by Harry2 on 2009-06-04
Ok thanks, what is a testdisk? (is it the downloaded one, burnt on a cd and then just use the test?!?!?)?

I cannot currently back up needed files, I dont have a 3.2 gig memorystick/psp/ipod/removable hard-drive...
Thats without music and such - Not important though lol

Why is it important to not use the hard disk to long to recover data?


btw, Thanks for all the help!

---

### Post by albinootje on 2009-06-04
> **Harry2 said:**
> Ok thanks, what is a testdisk? 

I've provided a link to testdisk earlier in this thread. Please read that page carefully.

You can make backups to cdroms, dvds, other harddisks, over the network (encrypt your files first) to "cloud" data storage. And if you don't have the media or the internet connection to back it up, ask friends to help you.

---

### Post by Harry2 on 2009-06-04
I would of realised about test disk :P

I remembered it as CGSecurity :P


Thanks!

---

### Post by Bnosidda on 2009-06-04
> **Harry2 said:**
>  I still have my dads stuff and photos so now all he will kill me for is not having windows


Kill you for deleting windoze? he should Praise you

---

### Post by Harry2 on 2009-06-04
nah, he drinks quite abit...

I dont really care for windows (except for gaming until wine) and its only for him/my sister who arent very computer orientated.

How do I install/run test disk?

Its only linux and not an exe, so 

sudo apt install testdisk

??

---

### Post by albinootje on 2009-06-04
> **Harry2 said:**
> nah, he drinks quite abit...

ouch :( Good luck with that.
> 
How do I install/run test disk?

sudo apt install testdisk


Yes, you would do exactly that in the "live session" ("Try without making changes").

---

### Post by Harry2 on 2009-06-04
live session?
argh I am too new to be doing this stuff :P

---

### Post by albinootje on 2009-06-04
> **Harry2 said:**
> live session?
argh I am too new to be doing this stuff :P

See attached screenshot for the "Try..without" option.

---

### Post by Harry2 on 2009-06-04
I used that for 30 minutes but it was too slow, having to load everything off of the cd :P

---

### Post by Harry2 on 2009-06-04
What is the install command, I have downloaded the linux test disk, I just need to know how to run/install...

---

### Post by albinootje on 2009-06-04
> **Harry2 said:**
> What is the install command, I have downloaded the linux test disk, I just need to know how to run/install...

Boot in Ubuntu from your hard disk, run :
```

sudo apt-get install testdisk

```
and see whether you can recover your data.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Harry2 on 2009-06-04
Thanks [albinootje]("http://ubuntuforums.org/member.php?u=628477"), Your a great helper!

But how do I start the application now?


nvm, trial and error ftw ;P

Now I just gotta get it too work (to suit my needs using the tutorial)

---

