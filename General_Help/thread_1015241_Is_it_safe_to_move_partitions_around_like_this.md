---
title: "Is it safe to move partitions around like this?"
date: 2008-12-18
forum: General Help
---

### Post by dorkdork777 on 2008-12-18
Hey, I've got a brand new computer sitting here and have a few questions ;)

I've moved my old 250 GB drive in along with the 500GB that came with it, so I've got all my old data, including my /home from my old Ubuntu install (yay!).

**(Question 1!)** My new computer is 64-bit, while my old one was 32-bit. Therefore all the data, config files, etc were made on a 32-bit install, and now they're going to be used with a 64-bit install. I've heard there should be no problems - is this true? Can anyone confirm this?
[B]
(Question 2!)[/B] Seeing as I now have two seperate drives, I need to plan my partitions. Now, as it is now, all my data is on the old drive, while the new one is empty except for an OEM install of Vista, which (gasp!) I'd like to keep. *expects death by stoning*

I'd also like my /home partition filling my 500 GB drive, to give me plenty of room. This means my Ubuntu and Vista installs will be on the 250 GB drive. My main question here is, could I safely resize and move the OEM Vista onto the 250 GB drive, and the /home to the new drive, using a LiveCD, without anything getting angry at me and blowing up my data? Is there anything I should be wary about?

Thanks a lot :)

---

### Post by dorkdork777 on 2008-12-18
Shameless horrific bump. I'd like to set this up ASAP; moving hundreds of gigs of data is something I like to do overnight. ie, now. If possible. :)

---

### Post by pietjanjaap on 2008-12-18
If you want to install the 64 bit version, you need to install on a empty drive. You can not use the old things.

---

### Post by dorkdork777 on 2008-12-18
Sorry, what's the old 'things'? Do you mean I can't use my old /home?

---

### Post by albinootje on 2008-12-18
> **dorkdork777 said:**
> Sorry, what's the old 'things'? Do you mean I can't use my old /home?
I think that you can probably use all of your /home after your new 64 bit installation without any problems.
I cannot imagine that certain applications would write specific 32 bit preferences in your /home which are not "compatible" in a 64 bit installation.

---

### Post by logos34 on 2008-12-18
no, you can use the old /home. 

Shrink vista down using it's own disk utilities.  Then make a new partition in the empty space (using gparted on the ubuntu live cd).  Copy /home to new partition using the link in my signature.  Remember to edit fstab.

So have you tried to boot ubuntu on the new machine? 64-bit machines run 32-bit fine, but the fact that the OS was installed/configured on another machine with different hardware may give some problems

---

### Post by dorkdork777 on 2008-12-18
Nope, I've left the old HDD untouched as of now. I'm gonna do all this partitioning stuff first, then install 64-bit Ubuntu - I'm posting from Vista (boo hiss boo). So I'm gonna have a fresh install of Ubuntu, using my old /home (thanks albinootje!).

What I mean is, will Windows stop working if I move its partition to another hard drive?

---

### Post by albinootje on 2008-12-18
> **dorkdork777 said:**
> 
What I mean is, will Windows stop working if I move its partition to another hard drive?

I don't know. I do know (iirc..) that Windows98 was more flexible than windows2000 when one would take a disk with it and put that disk in another machine.

But i can imagine that software like gparted can do that successfully.
Here are gparted's features mentioned :
[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

Hopefully someone else has the answer to your question.

---

### Post by dorkdork777 on 2008-12-18
I just thought there might be some problems with the boot.ini - or something. Can anyone confirm if there will/wont be issues?

---

### Post by logos34 on 2008-12-18
> **dorkdork777 said:**
> Nope, I've left the old HDD untouched as of now. I'm gonna do all this partitioning stuff first, then install 64-bit Ubuntu - I'm posting from Vista (boo hiss boo). So I'm gonna have a fresh install of Ubuntu, using my old /home

Oh, I see now...I thought you were just moving the 32-bit into the new x64 PC to run it there.
> 
I just thought there might be some problems with the boot.ini...

that's XP, vista uses a different system (BCDedit).  But if you move it to, say, the second partition on the other hdd, then you'll have to edit the appropriate file with something like EasyBCD

---

### Post by dorkdork777 on 2008-12-19
OK, I'm gonna give that a try. I'll move the partitions - all my really important data is backed up and I've got the recovery disc - and I'll just see how it turns out :) Many thanks logos34, and everyone else who replied! :D

---

