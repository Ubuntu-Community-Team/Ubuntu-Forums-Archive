---
title: "MediaDirect killed my Ubuntu install!!!"
date: 2007-06-22
forum: Dell  Ubuntu Support
---

### Post by Farenji on 2007-06-22
I hav a Dell Inspiron 640M, it came with windows vista but I removed that and installed ubuntu 7.04. During install I noticed there was an extra (hidden?) partition, which I removed. I created my own partitions, everything went well and my system worked flawlessly for weeks, until yesterday. When the laptop was turned off I pressed (more or less accidentally) one of the media direct buttons at the front and suddenly my laptop powered on. I didn't want that so I turned it off using the powerbutton.

When I booted the system again, I suddenly got a "dell media direct" screen (where the **** did that come from??), and after that an error telling me there was some error with some .dll file.

I rebooted and now I get a Grub error 17 everytime. :(

I used a ubuntu 6.06 live disk (no 7.04 at hand ATM) to get into my system but I noticed a new partition that looks like it contains windows stuff, probably the mediadirect stuff. Don't know where that came from, as I removed that partition during ubuntu install. The really bad thing is that this partition seems to overlap my root partition, which KILLED my linux installation, causing the error 17 from grub.

It's no big problem to reinstall, no data is lost, but I don't want this to happen again, so what I really want to know is this:

How can I *TOTALLY REMOVE* all media direct software? I don't want it, don't need it at all, and most important of all: I don't want that when I press one of the media direct buttons, it killes my system!!! When the system is off and I press one of the buttons, NOTHING AT ALL should happen. Now the buttons are turned into some sort of self destruct device and that sucks big time, to say it nicely.

Please help. Thanks!

---

### Post by ndrwgn on 2007-06-22
Sorry dude, but you can't.  The partition is hidden and protected, so a 100G hard drive is more like 90. it sucks, but what can you do?  all's I did was install entire hard disk, guided (7.04), and it works fine. All the media buttons work, and the only time I have trouble is when I try to do something new and "bleeding-edge".

You should just be able to reinstall grub with the live CD:

insert the cd, open a shell and type "grub"

Remember that for grub (hd0,1) means hda (primary controller master), second partition.

Now we need to tell grub where are the grub files:

If you know where they are, type something like:
root (hd0,1)

else if you have no idea, type:
find /boot/grub/stage1
and then the root command with the correct parameters:

setup (hd0)
to install it on hd0, that is MBR of the first HD.

type quit and reboot.

---

### Post by Farenji on 2007-06-22
Thanks for your reply. I know how to fix the installation, thats not the problem, but the next time I (or someone else!!) presses the media direct button with the laptop turned off, my install will be ruined again... Surely there must be some way to prevent this?

---

### Post by kwah on 2007-06-22
Had exectly the same problem. 

I put some info about it here: [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron640m](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron640m)

The thing is, I don't know what happened exactly and I can't reproduce the situation. The first thing I did, when I got my laptop, - installed Ubuntu immediately, first power up was with Ubuntu 7.04 Desktop CD followed by installation. It seemed strange, but at that time gparted did not recognize any existing partitions on the hard drive, I installed Ubuntu using the "whole" drive with manual partitioning. And then, after quite a while, MediaDirect button was pushed by me accidentally and Windows error message popped up :o

Fortunately, I was able to restore and recover all my data from the partitions found by **testdisk** (great tool!!!). I tried to reproduce the situation using recover disks supplied by Dell and a full reinstallation of the software, the only thing I could get similar to previous case is partitions not recognizable by gparted and thats it. Reinstallation of Ubuntu on top of the reinstalled set of software did not do the same trick I discovered by accident.

So, what I did is
```
dd if=/dev/null of=/dev/sda
```
then installed Ubuntu, afterwards I checked the disk by testdisk and only linux partitions are there. MediaDirect button now starts Ubuntu :D

---

### Post by Farenji on 2007-06-22
This sounds like a great advice, I'm gonna try this, thanks a lot!

---

### Post by Farenji on 2007-06-22
It also worked for me! The zero fill took 3 hours but now the media direct is gone, except for the logo (which will be in the bios I guess).

---

### Post by mike999999 on 2007-06-23
The media direct button turns the media direct partition on/off. If you tried it a second time, your system would have booted.

---

### Post by Farenji on 2007-06-23
> **mike999999 said:**
> The media direct button turns the media direct partition on/off. If you tried it a second time, your system would have booted.

No it wouldn't. I tried. The MD button not only turns on the DM partition but if it doesn't exist, it is re-created, no matter what data is on the disk. The ubuntu root partition was thrashed by this and the install was as dead as could be.

---

### Post by neptho on 2007-06-24
> **Farenji said:**
> No it wouldn't. I tried. The MD button not only turns on the DM partition but if it doesn't exist, it is re-created, no matter what data is on the disk. The ubuntu root partition was thrashed by this and the install was as dead as could be.

There are several reasons why this is improbable, if not impossible.  Check your partition labels.

---

### Post by Farenji on 2007-06-24
> **neptho said:**
> There are several reasons why this is improbable, if not impossible.  Check your partition labels.

That won't be possible as I zero filled the entire disk. Nothing to see there anymore.

But of course I checked the partition table before. Fact is that I removed all existing partitions during ubuntu install; ie the windows partition and a small FAT16 partition. I used the entire disk for ubuntu with manual partitioning and there were only linux partitions present after the install. But after pressing the MD button that FAT16 partition suddenly was back. Yes it's highly improbable (and it should be impossible!) that some Dell software kills your installation this way, without a warning, *but it did happen* and pressing the MD button again *did not fix it*.

---

### Post by kwah on 2007-06-25
I don't know why it is happened. I also tried to use MD button one more time - it did not fix the problem.

In my case unsolved questions are:
1. Why Ubuntu install (gparted in particular) started from the LiveCD at very first system power-up did not recognize any existing partitions? All Dell stuff should have been there at that time.
2. Why installation of Ubuntu using "the whole" drive with the formating of all partitions did not kill the hidden utility partition and the hidden MD partition at the end of the drive?
3. Why after the MD button was pushed the partition table was messed up? The problem was only with the partition table, as far as I can remember. Moreover, testdisk could find all linux partitions and restore the partition table layout bringing up my Ubuntu installation.

The only course of action I can imaging right now (I am not an expert in what is possible what is impossible) coming from the Dell factory hdd has layout like this:
1. DELL Utility partition ~2GB [hidden]
2. Windows installation ~all available space
3. MediaDirect ~2GB

Somehow installation of Ubuntu treated partition2 as a "whole drive" and installed there everything. GRUB installed to MBR.

MediaDirect button together with BIOS ??? messes up the parttition table layout assuming layout as it is done by default, there is no windows on partition #2 and hence MediaDirect just can't work, crashes and there is no way to get "good" partition layout back.

---

### Post by Farenji on 2007-06-25
There was one partition besides the windows partition when I installed Ubuntu. The other MediaDirect partition is on the "Host Protected Area", at the end of the disk which is a special area that's truly hidden from all utilities like gparted. The disk controller will actually lie about the true size of the disk to hide its existence. But it can't hide from a low level format. :)

[http://en.wikipedia.org/wiki/Host_Protected_Area](http://en.wikipedia.org/wiki/Host_Protected_Area)

---

