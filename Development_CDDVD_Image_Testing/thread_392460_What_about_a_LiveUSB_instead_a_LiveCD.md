---
title: "What about a LiveUSB instead a LiveCD?"
date: 2007-03-24
forum: Development CD/DVD Image Testing
---

### Post by Amphetamine on 2007-03-24
Hello,

as USB sticks are getting cheaper and cheaper I would like to use one as a LiveCD. Any suggestions how to accomplish that?

---

### Post by josephus on 2007-03-24
I don't have any experience doing this myself, but google turned up a couple of links

[http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB)

[http://www.ubuntuforums.org/showpost.php?p=1062799&postcount=100](http://www.ubuntuforums.org/showpost.php?p=1062799&postcount=100)

Sounds neat.  Would give it a try myself if I had a bigger USB key.

---

### Post by Amphetamine on 2007-03-24
> **josephus said:**
> I don't have any experience doing this myself, but google turned up a couple of links

[http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB)

[http://www.ubuntuforums.org/showpost.php?p=1062799&postcount=100](http://www.ubuntuforums.org/showpost.php?p=1062799&postcount=100)

Sounds neat.  Would give it a try myself if I had a bigger USB key.


Wow, great! Thanks for the links! Now I won't be bored this weekend! :popcorn: 

By the way, I bought an 1 Gig USB stick here in Germany at Saturn-Shop for 12 Euro and a few weeks ago I bought even a new 4 Gig USB stick at Ebay for 30 Euro, shipping included! And they are getting cheaper and and bigger every time! USB seems to be the future. And there are even 64 Gig sticks, but they still cost over 600 Dollar!

---

### Post by jerrylamos on 2007-03-24
Well, Puppy Linux has a setup for live USB which I've tried and it works.  In case the system doesn't boot from USB, you can make a diskette to boot and switch over to the USB and that works.  Nice, no noise, fast, and stores changes and files.  Even runs on an older PC that doesn't have a hard drive any more.  Also portable to different hardware.

I've seen ads for Knoppix Linux to purchase a pen with Knoppix already installed.  I don't remember the cost, but certainly higher than just the pen drive.  There's a Linux magazine article by Knopper on how to build your own Knoppix USB, and claims that there is a script on the latest Knoppix to help do it.  I haven't tried it.

On Ubuntu Wiki there are some complex involved setups for putting I thnk it was Xubuntu on a pen drive with a couple of different loaders.  I spent some time with that and couldn't get it to work.

Simply Mepis (a KDE Ubuntu derivative) claims to have a USB setup as well however I haven't found the "how to" yet.

Frankly, right now, persistent is broken on Feisty Beta.  I use it on Dapper and Edgy.  I've had a Feisty launchpad bug on persistent since Feb 10, with no luck yet.  Maybe they'll fix persistent for the ship version?  In any case it is more complex to set up and use than some of the competing Linux's.  

I'm sure that Ubuntu/X/K could be made to run from USB if there's some developer that's interested in it.  Sure would be handy, hardware independence.  Oh, well, I'm dreaming.  Cheers, Jerry

---

### Post by Amphetamine on 2007-03-25
Well, if I can't run Ubuntu on the USB like a LiveCD maybe I will switch to Knoppix but let's first give our best with Ubuntu. I am a beginner with linux so please don't wonder about my silly questions: How do I name the partition? The manual linked above by Josephus tells me: 
*The second should occupy the remaining free space and should be formatted with the ext2 filesystem and is given the name "casper-rw"* 
and that's what I want to do. If I only would know how to name it. I already partitioned it.

---

### Post by jerrylamos on 2007-03-25
Well, for persistent, the steps are like this:
1. Do df -h to make sure what the USB drive name is.  Expect /dev/sda1 which is the first partition on the USB
2. sudo umount /dev/sda1
3. sudo mkfs.ext3 -b 4096 -L casper-rw /dev/sda1
That gets a volume label casper-rw on the USB.
If persistence worked, then reboot, F6, add persistent to the list of options, preceded by a space.

From that, I might infer if you wanted to format the second partition, and give it a label, you could try:
df -h to see what's mounted?  Maybe /dev/sda1?  What about /dev/sda2, the second partition?  Anyway,
sudo umount /dev/sda1
sudo umount /dev/sda2 (if it's mounted)
sudo mkfs.ext2 -b 4096 -L casper-rw /dev/sda2
wait for it to complete.....
Now my USB is set up with only 1 partition so I can't test this.

Reboot and see what you get.  That's a bit easier than fussing with mounts & stuff.
For a lot more detail, see:
[http://www.ubuntuforums.org/showpost.php?p=1229101&postcount=158](http://www.ubuntuforums.org/showpost.php?p=1229101&postcount=158)
and
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
Good luck.  I haven't had any with the Ubuntu USB live yet.
Cheers, Jerry

---

