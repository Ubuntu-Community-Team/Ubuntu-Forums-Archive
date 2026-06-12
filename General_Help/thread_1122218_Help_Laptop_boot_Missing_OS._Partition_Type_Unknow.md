---
title: "Help?? Laptop boot: Missing OS. Partition Type: Unknown"
date: 2009-04-10
forum: General Help
---

### Post by MrSootentai on 2009-04-10
I'm not really sure where to start, but I rebooted my laptop today after it was in hibernation and first thing I noticed was that my wallpaper, icons, and generally ever normal thing my Gnome desktop boots with was gone. So I hunted around and found that 'killall nautilus', but it actually didn't.
Next thing I noticed was that Update Manager was displaying in error saying it could not locate the cache, and I should try 'dpkg --configure a' to fix it. But that didn't do much of anything to help me.
So I decided to reboot it once more, and this is where I'm at now, my laptop boots with 'Missing Operating System' and when I use Gparted LIVE to check the partition, the partition type is listed as 'unknown'.
Now I'm stuck as to what to do. I didn't play around with any partition editors or filesystem editors before to allow this to happen.
I have no problem reinstalling everything from scratch. But what I need to know is, is there any way to recover the files from that 'unknown' partition (it was EXT3).
I have some real important files on there, and before anyone gets on a tangent about backing up, thats exactly what I was doing last night before this problem occured(just flat out dragging-and-dropping the important stuff onto my MyBook).

---

### Post by zephyrcat on 2009-04-10
That sounds like a crashed hard disk to me. Did the laptop suffer any physical damage? I put my elbow down on the palm rest of my Dell M1530 and destroyed the hard drive beyond recovery, so it is definetly possible.

Does the hard drive make any bad sounds?

You could try something like this:

[http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html)

Above all, don't stress the hard drive unnecessarily. If it is indeed crashed, too much activity on the drive could cause furthur damage.

Depending on the value of the data, you might also consider going to a professional data recovery service.

---

### Post by MrSootentai on 2009-04-11
Well I know for a fact the hard drive isn't physically damaged because I have another partition, a Dell Ubuntu recovery partition, that is still accessible. 
The attached screenshot is a look at what GParted shows me. The 149GB partition is the one I am trying to access.

---

### Post by callie510 on 2009-04-11
Just cause you can get to one part of the disk doesn't mean another part isn't damaged... but I see your point, a catastrophic failure like that probably would have affected more.

Try "testdisk". This utility has helped me out in a pinch when my partitions became unreadable. I ran it off the "Ultimate Boot CD" (just google it and boot off it) - hopefully it will see your partition and correctly relabel it ext3.

If you still have trouble, there are rescue programs on that disk (I think) that will help you save files. Let me know if this doesn't work and I will find links to data recovery programs that have helped me in the past. 

My sister stepped on her iPod once and I managed to recover her whole library except 5 songs :) Data recovery is always possible to some extent if your hard drive still spins and connects to the computer!

---

### Post by MrSootentai on 2009-04-11
Thanks callie510!
So TestDisk is actually recognizing the partition, but I'm not sure what to do from there now. I can even browse the partition through TestDisk, but I'm not sure how I can make the partition accessible through another OS running from a live cd. (NOTE: It only found the partition after I did the first search, then ran a deeper search)
The partition, is marked with 'P' for Primary under TestDisk and that's as far as I've gotten.
What should I do from here?

---

