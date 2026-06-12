---
title: "iOmega External HD problems."
date: 2009-01-17
forum: General Help
---

### Post by AICollector on 2009-01-17
Ok, after buying an external HD, I backed up my data onto it, now, sadly, with Ubuntu degrading rapidly because it dosent like being a hybrid (running 32 bit apps on a 64 bit system) and myself wanting to switch to 32 bit, I can honestly say I'm stumped, heres my problem;

The external HD, as you might expect, is FAT32, sadly, when I need this drive the most, Ubuntu is declaring it read only and telling me the filesystem is acutally MSDOS. This worries me.

Likewise, the HD has been flaky, it turns itself off, regardless of whether I'm not using it, or if I'm writing a file to it.

Anyway, now that it has gone read-only, I thought I might as well replace FAT32 with EXT3, following a how-to, I installed and used gparted, (to illusrate just how badly degraded my system is, gparted can only be run once per session for some strange reason) following the how-to and unmounting it means gparted should scan for drives.

Whereas the first time I ran gparted, it did this in under 30 seconds, now, however, it is not doing it at all and seems to be continusally looking for drives.

So, I'm stuck, I cannot spend too much time on this system as Ubuntu is failing, fast. (programs failing to load, files going missing, etc).

So, I'm stuck, I can't find a howto or tutioral or anything on how to format the disk and replace it with ext3 through the command line. (How I wish Ubuntu had a 'format' option!) 



Sidenotes; 

the reason I want ext3 is because many of my files are larger then the 4.1 gig limit that FAT32 can take.

I'm moving to 32 bit because of the annoying amount of hacking I have to do to get 32 bit apps working (not only Skype, but programs off sourceforge, etc)


As you might expect, I'm sworn many times at this blasted machine, and I hope and pray one of you kind souls can help me.

---

### Post by vanadium on 2009-01-17
You can format a disk with the "mkfs" command.

For this, you first need to know its device name. "blkid" is a convenient way to list all partitions your system sees.

```

sudo blkid

```
will show the partitions. Assume the partition is /dev/sdc1

```

sudo mkfs -t ext3 /dev/sdc1

```

will create an ext3 file system om /dev/sdc1.

If your system is totally unstable, then reinstall.

---

### Post by Bucky Ball on 2009-01-17
Sounds possibly hardware rather than soft.

---

### Post by AICollector on 2009-01-17
It may be interesting to note that on the box for it, it is stated that you need Windows or OS X, I don't know if this is trying to overcompensate for user-stupidity or if it is anti-Linux, either way, it dosent like Linux.


Yes, i'm planning a reinstall, but data needs somewhere to go :P

Anyway, thanks for your help, the terminal accepted the commands and is now loading ext3.

---

### Post by dhughes on 2009-01-17
I don't know if this helps or not but I bought a LaCie 1TB USB external drive and it came with a lot of junk on it for formatting it and setting it up under Windows or OS X, and there were a couple of partitions on it too. I used an Ubuntu LiveCD, selected Gparted and formatted the drive as ext3, wiping out everything on it, it works great on Ubuntu 8.10

 If your system is going downhill why not use an Ubuntu LiveCD since it has Gparted on it to format the external drive and then transfer files to the newly formatted external drive? You wouldn't have to worry about your system crashing since you would be using the LiveCD not Ubuntu installed on your hard drive.

---

### Post by AICollector on 2009-01-17
Ok, now I'm really stuck, just after I posted my reply above, my system froze and I had no choice but to reset.

Now the external HD isnt even being recongized.

Great times, great times....

---

### Post by dhughes on 2009-01-17
> **AICollector said:**
> Ok, now I'm really stuck, just after I posted my reply above, my system froze and I had no choice but to reset.

Now the external HD isnt even being recongized.

Great times, great times....

 Do you have a LiveCD?

---

### Post by AICollector on 2009-01-17
I do, but that can't find the external HD either.

---

### Post by dhughes on 2009-01-17
> **AICollector said:**
> I do, but that can't find the external HD either.

 Look in /media for the external drive, or even Gparted to see where the drive is, select the drop down box on the right side and you can tell by the drive size e.g. if you see a 250GiB device on /dev/sdd then I'd say that's it just don't format it by mistake if you have data on it :P

---

### Post by AICollector on 2009-01-17
uuhhh...I'm sure I mentioned before, but gparted (on the system or the LiveCD) cant find the external drive.

and no, it's not in /media.


It's just turning on and turning off by itself, my system is failing, and right now, Windows is looking mighty tempting, at least I knew WHERE to bash with a hammer.

---

### Post by Bucky Ball on 2009-01-17
Sounds like the drive. Can you try it out on another computer? Apologies if you have done this already.
You might find windoze makes no difference if it is a hardware problem - switching on and off by itself?

Got another cable to try, perhaps? Power adapter for the external drive?

I would unplug it immediately and check that your system runs without it. If so, check the drive on another before it screws up anything other than itself.

---

### Post by sedawk on 2009-01-18
I recommend to run a LiveCD instead of the "broken" installation
on your hard disk to do the backup.

For debugging purposes have a look at the output seen with "dmesg".

Are you connecting the HD to frontside or backside USB sockets? Frontside
sockets are known to have bad internal cabling, so do not use them for
USB 2.0 harddisks - a frequently disconnecting drive can be caused
by a broken USB cable. Try to use a backside USB socket!

Connect the USB drive after the system (LiveCD) is up and running,
then you can see what happens when connecting the drive from "dmesg".

---

### Post by AICollector on 2009-01-18
I attempted switching the ports, no luck. Drive is just as flaky.
Ubuntu isnt picking the drive up at all. CLI or GUI tools are having no luck. The drive does not exist, according to Ubuntu.


As a side note; I don't suppose anyone knows why the system would suddenly become very unstable (to the point of not even being able to boot up sometimes) as soon as a 32-bit program is installed?

---

### Post by Bucky Ball on 2009-01-18
What are the exact details of your machine and what version of Ubuntu have you got installed?

---

### Post by dhughes on 2009-01-18
> **AICollector said:**
> ...As a side note; I don't suppose anyone knows why the system would suddenly become very unstable (to the point of not even being able to boot up sometimes) as soon as a 32-bit program is installed?

 Corrupt install perhaps? It's happened to me, you download the iso, burn it to a disk and somewhere along the way something goes wrong.

 I'd say you download a new iso, burn it, check it and see if you can use Gparted with the new LiveCD and if it detects your external drive and also if your system is system is still acting weird.

---

### Post by AICollector on 2009-01-19
Laptop is an Asus X50 GL.

Running Ubuntu 8.10 64-bit, with some 32 bit apps like Skype.


All performance issues aside (only focusing on usabilty), what would you recommend for a reinstall? 32 or 64?

---

### Post by Bucky Ball on 2009-01-21
64. You might find this of interest if you are having Skype-type problems but for most people (myself included) it runs fine on 64bit and the Skype folks will get round to a 64bit version one of these years! 

[http://forum.skype.com/index.php?showtopic=77318&st=0](http://forum.skype.com/index.php?showtopic=77318&st=0)

---

### Post by AICollector on 2009-01-21
Hmm...2007, a bit dated, but at least they arnt ignoring the problem completely. 

Well, thats odd, I thought Skype was the reason my system was flailing about with it's arms in the air, dependcies breaking and programs failing.
(the reason I suspected as such was because Skype was the last 32 bit program installed, and was less then five mins old when things started to  go flaky)

---

### Post by Bucky Ball on 2009-01-21
That thread is not dated by the end if you have a look at the last few posts. It goes to 08 and Skype still haven't managed to come up with anything (and now it's 09). Thought they'd placate the Linux community with video calling, but I couldn't be bothered about that.

Skype might have been a coincidence. One sure fire way to find out is to uninstall it (the deb is easy to install again as you probably know). Did you download any updates before chaos happened? Plug in anything new, do anything at all differently???

---

### Post by AICollector on 2009-01-22
Ahhh..yes, I see....well, thats not good..

Yes, Ubuntu informed me it had an update for my battery monitor as well as other systems that seem vaugly graphics related, but I cannot remember them.

I'm afraid that I don't have the knowledge to uninstall dependancies (unless Synaptic handles those as well?)

Going back over Firefox's history, I can see I downloaded Skype through the CLI using a HowTo for Dapper Drake.

---

### Post by Jordubu on 2009-01-24
[B]All right guys,

This is what i did and it works[/B]

I have an Iomega external Hard Drive (HD USB) 250 GB
I downloaded **“GPARTED”** then it identified my Iomega HD
[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")
Then I rightcliced it and UNMOUNT it That’s necessary for the formatting
Finally rightcliced again and select format to FAT32 that’s the needed one format
This FAT32 allow you to write and read it.

And it works with **Ubuntu** and
**Windows** and I supose to **MAc OS X** too
So that is it[B]
Remember to make a BACK UP first with DVDS or another Computer or HD[/B]

---

