---
title: "[SOLVED] Testing a software RAID 1/Failure simulation"
date: 2008-12-10
forum: General Help
---

### Post by Weidbrewer on 2008-12-10
I currently have mirrored 500 GB drives running in my server (8.04 LTS.)  I set them up with the _[linked instructions]("http://nodebox.metaforix.net/articles/running-software-raid-on-ubuntu")_, and everything works great - has been for most of a year.  Later this week, I will be installing two 1TB drives the same way, and this time trough, I'd like to be a bit more thorough.  What would be the best way to simulate a disk failure and then "recover" data?  

Given the size of these drives, and amount of data that will be on them, I want to make darn sure that the RAID works.

Thanks in advance for the help.

---

### Post by fjgaude on 2008-12-11
If you boot from a raid1 array make sure to have grub on both drives so if one failed, you will not know which one, you can still boot.

Reading the mdadm **man** pages we see we can fault and then remove a drive without physically taking the drive out of its sockets. Then we can add a new one back as needed.

In raid1 either of the two drives have all the data.

For important data backups are absolutely necessary. Many have three, one online, another near-line, and finally, offline.

Good luck!

---

### Post by Weidbrewer on 2008-12-11
Thank you for the reply, but that unfortunately doesn't answer my question.

I am trying to simulate a total drive failure.  What I would like to do is be able to have one drive "fail" and reformat it so that it would be as if I was replacing a smoked drive with a totally new one.  I want to see what I would need to do to recover from something like that and make sure the software RAID actually works.

Background:  I realized that with the 500GB RAID, I had all of the information duplicated on the other drive, but I was taking a lot on faith that I could recover if one drive went.  Before I set up the new one, I want to be able to run through it before I transfer over all the important data.  I know that on the server boxes with hardware RAIDs that I've used, all I have to do is unplug a drive, let the system realize it's gone, then slot in a blank formatted drive and it just goes about rebuilding the RAID.  I doesn't seem to me that this would work with a software RAID.  Make sense, or did I just overly confuse the issue?

Also, no, I maintain my OS, Grub, etc on a separate drive to avoid exactly what you mentioned above happening.  (I maintain a separate back-up of that for emergancies as well.)

---

### Post by moberry on 2008-12-11
You can set a drive as faulty and remove it, add others with madadm.

I think its like this:

mdadm /dev/md0 -f /dev/hda1

---

### Post by Weidbrewer on 2008-12-11
Just to make sure I follow:
```
mdadm /dev/md0 -f /dev/hda1 
``` - obviously with drive names modified to fit situation - this will add a blank disk to an exsisting array?  Will it then automatically populate it with the data?

Thanks for the help, you two.

---

### Post by fjgaude on 2008-12-11
The mdadm man pages have all that is needed to do as you wish, a fragment:

```

MANAGE MODE
       Usage: mdadm device options... devices...

       This usage will allow individual devices in  an  array  to  be  failed,
       removed  or  added.  It is possible to perform multiple operations with
       one command. For example:
         mdadm /dev/md0 -f /dev/hda1 -r /dev/hda1 -a /dev/hda1
       will firstly mark /dev/hda1 as faulty in /dev/md0 and will then  remove
       it  from the array and finally add it back in as a spare.  However only
       one md array can be affected by a single command.
```

Is this it?

---

### Post by pietjanjaap on 2008-12-11
Search for problems for your hardware, name harddisk and controller.
Like f1 samsung harddrive and intel raid controller some have problems, looks like f1 samsung is not ok.

---

### Post by Weidbrewer on 2008-12-11
**fjgaude:**  I think that one or the both of us is missing something that the other is trying to say.  Yes, I read the man pages, but they did not answer my question, which is why I started this thread.  However, I'm not explaining myself well.


From what the pages say to me, all I am doing "failing" a drive in name only.  All the data is still there on it.  After "failing" it, I test, the RAID says "whoops,there's a problem,  I re-enable it and the RAID says, "all better now."   I'm looking to actually, physically wipe and reformat one of the drives and rebuild from there.

An analogy:  Say that the RAID is a light bulb,and I want to practice what I will do when it burns out.  I could flip the switch and I'd see what it was like in the dark - but I still wouldn't know what it's like to unscrew the bulb and put in a new one.

It seems like the example that you gave is to just test the software, which is what I'm not fully trusting.  I want to put some data on the array, fail a disk, completely wipe it clean format it, then replace it in the array as if it was a brand new disk that I just bought.


If that is what your example accomplishes, then this was totally just me not catching that (which I would not put past myself), and I apologize.

---

### Post by nzadLithium on 2008-12-11
is your software raid across two entirely seperate hard disks? If it is take a look here:
[http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill](http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill)

That page has instructions how to overwrite your hard disk with 0's, which will destroy all data on it in such a way that its pretty much impossible for the average person to get back. XD To recover from that you would need to have some crazy machine that can read minor differences in residual magnetic forces on the hard disk (ie CSI type stuff :p) XD

Is this what you wanted? Remember this will DESTROY all data and boot information on the disk and you would have to be insane to want to do it :)
(Please moderators don't kill me for posting this :S).

---

### Post by Weidbrewer on 2008-12-11
Okay...now we're getting somewhere...we just need to dial it back again.  (I almost feel like I'm firing artillery barrages here.  I didn't realize it was such a difficult question.:p)


Let's try this yet another way:  Forget the word "test."   Let's say that one of my two disks died tonight.  Tomorrow, I buy another one - How do I incorporate the new on in to the RAID and rebuild?

---

### Post by nzadLithium on 2008-12-11
I know pretty much nothing about RAID but I did a quick google search, and found this:

[http://radu.rendec.ines.ro/howto/raid1.html](http://radu.rendec.ines.ro/howto/raid1.html)

It looks like its helpful to you :)

---

### Post by fjgaude on 2008-12-11
Great, a really good link for those wishing to boot from a raid1 array, and then know how to recover from a disk failure. Thanks, nzadLithium!

---

