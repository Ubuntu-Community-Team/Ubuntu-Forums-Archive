---
title: "Is there a good, free, program that give read/write access to ext3 from windows?"
date: 2009-01-24
forum: General Help
---

### Post by markjs on 2009-01-24
I obviously can access my vista drive from ubuntu, but I'd like it to go both ways.  I use both, but sometimes it's handy to be able to get at something without a re-boot.  It's also nice, since I am yet learning ubuntu to be able to take a note in windows and then save it on the ubuntu drive for later reference, although my need for writing files to the other drive are not likely to be much, still it'd be nice to have.

---

### Post by taurus on 2009-01-24
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by markjs on 2009-01-24
I just found that and for some reason it doesn't work.  I can see the drive now, but Vista thinks it needs to be formatted?!?

---

### Post by markjs on 2009-01-25
Could it be because I have Vista Business x64 and ubuntu for 64 bit?

---

### Post by mb_webguy on 2009-01-25
Quite possible.  It wouldn't matter about Ubuntu (since there's no difference in the filesystems on 32- and 64-bit systems), but Windows is notoriously bad when it comes with compatibility with 64-bit systems and software.  

However, have you read the [troubleshooting page]("http://www.fs-driver.org/troubleshoot.html") for ext2ifs?  The first Q on the FAQ seems to address your problem.

---

### Post by vagrahb on 2009-01-25
I have been using Linux Reader for quite some time to read my linux partitions works pretty well with vista and with xp.

[Linux Reader]("http://www.diskinternals.com/linux-reader/screenshots.shtml")

---

### Post by markjs on 2009-01-25
This sucks!

[IMG]http://farm4.static.flickr.com/3338/3225283752_e8733718ac_o.jpg[/IMG]

---

### Post by markjs on 2009-01-25
There may even be another issue.  I had never had a RAID setup before and I tried it for a while, but it really made no difference for me so I went back.  Linux Reader still sees the ubuntu drive as part of a stripe RAID setup!  How can that be?  I allowed ubuntu to overwrite the drive completely and RAID is not enabled?!?

---

### Post by fjgaude on 2009-01-25
I assume you used **mdadm** to create software raid? Whatever the name of the array, e.g., /dev/md0, unmount it, stop it, and then use mdadm to zero the superblocks on each drive.

Just putting in a new filesystem doesn't remove the special superblocks that raid uses.

If you need a command-by-command listing of what to do, ask.

The **man** pages for mdadm shows much about software raid.

---

### Post by zvacet on 2009-01-25
You can try [this]("http://sourceforge.net/projects/ext2fsd") and see if it work.

---

### Post by markjs on 2009-01-25
> **fjgaude said:**
> I assume you used **mdadm** to create software raid? Whatever the name of the array, e.g., /dev/md0, unmount it, stop it, and then use mdadm to zero the superblocks on each drive.

Just putting in a new filesystem doesn't remove the special superblocks that raid uses.

If you need a command-by-command listing of what to do, ask.

The **man** pages for mdadm shows much about software raid.

No I meant RAID with the Nvidia drivers in Vista is when the RAID array was created, it was never done in ubuntu.

---

### Post by fjgaude on 2009-01-25
Oh boy! There is a program called **dmraid** that folks use to access fakeRAID created in the BIOS for Windows. It's in the repository:

```
sudo apt-get install dmraid
```

After you get it you can read the man pages for it and be on your way.

---

