---
title: "When the Hard Disk is Full, Ubuntu Refuses to Boot Up..."
date: 2006-07-10
forum: Desktop Environments
---

### Post by rykel on 2006-07-10
Hi there,

This has happened on a couple of occasions, and I hope the next version of Ubuntu will remove this bug...

Whenever my hard disk containing root (/) filesystem reaches 99% full, Ubuntu refuses to boot up. It normally stops at "Checking all filesystems..." without moving into the GNOME Desktop Manager Login Screen.

I am NOT sure if the error has to do with the hard disk space actually, but the problem goes away when I uses a live CD and removes some big files from the root (/) partition.

Simply for comparison sake, Windows XP will also behave strangely and crash/hang/mess up the screen when C: reaches 99%, but at least Windows will load the GUI, so we can still delete stuff without resorting to a live CD.

Do you have this incident to report, or is it just my hardware?

[-o<

---

### Post by lamego on 2006-07-10
If you get your / full then you have a problem wich is causing it, getting the / is a result of the problem , not the problem itself.
This big files you mention are they logfiles ? If so did you checked what was added to make them so big ?

---

### Post by rykel on 2006-07-10
> **lamego said:**
> If you get your / full then you have a problem wich is causing it, getting the / is a result of the problem , not the problem itself.
This big files you mention are they logfiles ? If so did you checked what was added to make them so big ?

Hi there,

OK let me explain... my / and /home are all on the same partition. Thus, when my files fill up /home, it is the same as / becoming full.

Therefore, / full is the problem itself, I believe. UNLESS there are some other reasons why my boot up would work today, and stop working tomorrow without warning or signal. If so, then it would be even more scary, since removing files from the partition can still be done relatively easily with Knoppix etc.

p/s. the big files can be anything, usually my VCD collections, which i copied over.   :)

---

### Post by aysiu on 2006-07-10
Buy a bigger hard drive? Set your package manager not to keep .deb files? I don't think you should be toying around with the 99% level of use in either Windows or Ubuntu.

---

### Post by rykel on 2006-07-10
> **aysiu said:**
> Buy a bigger hard drive? Set your package manager not to keep .deb files? I don't think you should be toying around with the 99% level of use in either Windows or Ubuntu.

hehe, tat's true... money solves everything, eh?   =)

but seriously, i think ubuntu should at least boot into the GUI and inform the user that she is going to C-R-A-S-H.   ;)

---

### Post by aysiu on 2006-07-10
File a bug report/feature request. Maybe they can put that in for Edgy+1.

---

### Post by DaveNF2G on 2006-07-13
In the meantime, how does one recover space on the hard drive when it's full and the operating system won't run?

Advising to buy a new drive, or to avoid getting the drive full, is cute but not helpful.

---

### Post by aysiu on 2006-07-13
Do you have a live CD? Can you boot into recovery mode?

The .deb files in /var/cache/apt/archives generally take up a lot of space, so you can manually delete those with a live CD, or delete them with one command in recovery mode: ```
apt-get clean
```

---

### Post by maddbaron on 2006-07-14
> **aysiu said:**
> Do you have a live CD? Can you boot into recovery mode?

The .deb files in /var/cache/apt/archives generally take up a lot of space, so you can manually delete those with a live CD, or delete them with one command in recovery mode: ```
apt-get clean
```


I have thae this problem...my root and home are on separate partitions. now my root is full. has a lot of logs taking up space.

how do i remove them?

and i dont know if their are .deb's in there would that code work also?

i get to login gui enter everything press enter but splash page was coming up then stopping now its not coming up at all.

i gotta empty this root. or combine it with my home.

can i use live cd to do anything without reinstalling?

---

### Post by maddbaron on 2006-07-14
it worked! but now it looks like my system was completly rebooted.

---

### Post by scxtt on 2006-07-14
what you're experiencing is COMPLETELY NORMAL action for any OS ... if your F/S is full or approaching full (i.e. 99%) how can you expect the OS to function? -- it still has to write files when you login, which isn't very possible if your F/S is full ...

this is NOT a bug or a problem w/ ubuntu - it's fully a result of an unrealistic user expectation ... i have production boxes that behave in the exact same way, that's just how it works ...

aysiu's suggestion of 'buy a bigger hard drive' is right on the money ... if you have large files you want to keep, then expect them to fill up your hard drive ... otherwise remove the .debs or log files or core dumps ... just don't expect a gui to tell you something you should already know (your HDD is full) ...

---

