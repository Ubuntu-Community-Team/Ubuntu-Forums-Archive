---
title: "boot problem"
date: 2009-05-31
forum: General Help
---

### Post by kornny on 2009-05-31
hi to everyone...

i have a boot problem... i have ubuntu installed on my computer. i have 2 harddisks. 1.st one&#305;nstalled xp the second one is &#305;nstalled ubuntu 9.04. before half an hour i just format the xp. after that i cant see ubuntu boot loader screen and i cant choose ubuntu on the start up when i turn on the pc. &#305; just can see ubuntu w&#305;th the l&#305;ve cd. and &#305; dont want to re&#305;nstall ubuntu. how can &#305; make the boot loader screen works on the start up. &#305; tr&#305;ed to do &#305;t from the b&#305;os &#305; make the sata2 dr&#305;ve f&#305;rst boot but &#305;t d&#305;dnt work. have any &#305;deas???????

---

### Post by mhgsys on 2009-05-31
You should reinstall grub on the disk which has ubuntu on it, that's the best way I guess, leaving the other disk free to to whatever you want to do with it.
meaning you should adjust your bios to boot from hd1. (in your case sata 2 right?)

Remember, If you want to install windows again on the other disk, it needs to be primary,(hd0) when installing the OS, later on you can use the map commands in grub to make it believe it's still hd0.

I suggest:

 reinstall grub on (hd1).
 **so the setup command; setup (hd0) would be setup (hd1) then**



Anyway: to recover grub :

Bootup a live cd, open a terminal and do the following.

```
sudo grub
```
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr 


```
setup (hd0)
```
Finally exit the grub shell
```

quit

```

---

### Post by blueridgedog on 2009-05-31
mhgsys steps should get you working as it is more than likely simply the case that your xp format wiped the master boot record of your first drive.  For sake of clarity, if you follow the steps, you will be installing grub back to the master boot record of the first hard drive, which may or may not be the one with ubuntu on it, but it will point to the hard drive where ubuntu is.  Good luck.

---

### Post by mhgsys on 2009-05-31
@ blueridgedog
> **blueridgedog said:**
> mhgsys steps should get you working as it is more than likely simply the case that your xp format wiped the master boot record of your first drive.  For sake of clarity, if you follow the steps, you will be installing grub back to the master boot record of the first hard drive, which may or may not be the one with ubuntu on it, but it will point to the hard drive where ubuntu is.  Good luck.

I guess you didn't notice my little story before the commands.

I suggest:

reinstall grub on (hd1).
**so the setup command; setup (hd0) would be setup (hd1) then**

---

### Post by blueridgedog on 2009-05-31
I stand corrected.  But still believe that the OP needs to setup hd0, as that is probably the boot drive from the system  (ie...the instructions will work).  Putting grub on hd1 probably will not change the boot issues.

---

### Post by Liuxurong on 2009-05-31
@2

Thank you!!!

---

### Post by mhgsys on 2009-05-31
> **blueridgedog said:**
> I stand corrected.  But still believe that the OP needs to setup hd0, as that is probably the boot drive from the system  (ie...the instructions will work).  Putting grub on hd1 probably will not change the boot issues.

meaning you should adjust the bios to boot from hd1. (in this case sata 2) 
?
lol.

I'm pretty sure grub can be installed anywhere you want it, 
anyway; you still didn't read my little story did you?

---

### Post by blueridgedog on 2009-05-31
I did read that you were instructing the OP to install the boot loader to the second drive, and then adjust the bios to boot from that drive, but posted instructions for installing the boot loader to the first drive.  I generally recommend putting the boot loader onto the first drive as it makes future trouble shooting easier (when the OP comes back with another issue).  The instructions are great, I just don't recommend installation onto hda1/sata2/sdb.

---

### Post by mhgsys on 2009-05-31
@blueridgedog

That I understand completely.
And that's the reason why I posted instructions to setup grub hd0, and wrote my little story above it.

To not have people reading: anyway to restore grub; and cut paste the commands to set up on hd1.
Thats why I added ** *so the setup command; setup (hd0) would be setup (hd1) then**  in the beginning of my story.

Anyway; Good that you noticed that I said to setup on second disk and posted instructions to setup hd0
Hope you now understand why.

Anyway; He could also physically  place the disk to be hd0. 
I just thought this was the easiest way to go in this case

---

### Post by blueridgedog on 2009-05-31
Actually, just watching the conversation will help new users understand about booting order and master boot records.  The reality is that you could put any loader in any disk and point the bios to it.  It was once so simple when systems only booted from the first disk!  But I date myself...

---

