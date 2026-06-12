---
title: "removing ubuntu"
date: 2006-01-02
forum: General Help
---

### Post by Generic1234 on 2006-01-02
I installed ubuntu on my computer, but have now decided that I would like to remove it (sorry!), at least until I have better technical knowledge of computers.  Currently every time the computer starts I use the boot loader menu to start windows xp.

I tried using the partitioning tool on the ubuntu install disk to remove the linux and swap partitions and enlarge the windows partition again, but it didnt really work.  I think the windows install disk cant repartition the hard drive without deleting my existing windows partition as well, so i dont really want to do that.  I figure i'll use some other repartitioning program i'll find on the web.

But first, is there anything else I will have to do to make sure my computer works after partitioning?  Like configure the computer to start windows straight away, rather than trying to start the boot loader (which will be gone after partitioning)?  Help appreciated.

---

### Post by encompass on 2006-01-02
I would recommend googling this.... there is a thing you will have to do to format the MBR(master boot record)  format -m or something like that.  and for the resizing?  You may want to create a new partition anyways, due to unreliables computers nowaday... having another partition in fat32 or some other kind gives you the ability to backup and save your data... so that when you do reformat your first partition you don't lose anything.  Don't you think that wouod be nice.  'linux has done it for yours, you thin windows would have caught on to it by now)

It is a bummer to see you leave the linux world.  beings this is your first post on the forum, you haven't really had a good taste of the costumer service provided here.  It is some of the best your ever going to see.

---

### Post by kingsidy on 2006-01-03
i think in order to that kind of stuff like claiming back linux partitions, it is better to use tools like partition magic. But before you do, first repair the MBR, by inserting a windows xp cd, select reconvery console and then select the c drive once you are there you'll have a command line. Type in fixmbr then press enter. Then reboot. when you reboot you won't get the grub menu list anymore. Then delete the linux partition and swap by using tools like partition magic and things. Can't think of a better program at this time.

---

### Post by twokatmew on 2006-01-03
Go buy a copy of Partition Magic 8.0 and install it on Windows.  It will allow you to repartition your hard drive(s) without destroying data.  Once you've got your partitions the way you want them, create a DOS/Windows boot disk with the FDISK program on it, boot from it, and enter the command FDISK /MBR.  That will restore the original boot loader so Windows starts automatically.  (If you Google "FDISK," you'll see there are free enhanced FDISK programs out there.)  

Personally, I hate Symantec, which bought out PowerQuest (company that created Partition Magic).  Acronis makes a similar program called Disk Director Suite 10.0 that I hear works great.  (I still own PM from the days before Symantec took over.)  I do use Acronis True Image 9.0 to create disk images, and it works very well, no complaints.  Additionally, Acronis software is less expensive than Symantec's.  I got an even better deal on True Image 9.0 at Newegg.Com, but I just checked, and they don't sell Disk Director.

Hope this helps,

---

### Post by PryGuy on 2006-01-03
Boot from DOS (hope you know how to do it) and type ```
fdisk /mbr
```then reboot.
Ubuntu is great, you make a big mistake...:(

---

### Post by Generic1234 on 2006-01-03
Thanks for the help everyone!  I did what kingsidy said, and it worked.

I plan to move over to linux some time, just not right now.  I figure open source is the way to go, since then code can be improved, rather than hidden away like proprietry stuff.  Also the fact that you guys helped me go back to windows shows how projects like ubuntu are better for end users than commercial stuff - can you imagine microsoft helping people install linux on their computers?  unlikely.

Anyway thanks again, and rest assured I will go back to linux some time in the near future.

---

### Post by chocolatetoothpaste on 2006-01-03
It would actually be better to just dive into linux now if you plan to anyway.  Because then you won't have to re-learn things that windows taught incorrectly anyway.  It will save a lot of time and be much more rewarding.  that is my humble opinion.  hope to see you around here still.

---

### Post by PryGuy on 2006-01-03
That is right, and you realize how dumb and wrong Windows is when you dive into Linux. "Windows is money, Linux is philosophy" as I say. Micro$oft will *never* be able to solve their Windows security problems unless they get their kernel *completely* rewritten.

---

### Post by cvcaelen on 2006-01-03
By now, it's too late, you've removed Ubuntu,
but
why not let it sit on your PC
and 
time permitting learn to use it?
sure wouldn't have harmed anything

Christiaan

---

### Post by Lord Illidan on 2006-01-03
I agree. How about telling us your problems here, for example? Or look up on the wiki?

---

### Post by kingsidy on 2006-01-03
even if you went back to xp, i would recommend installing ubuntu in vmware. You can then use linux within windows if you have the ram to do so. Once you become familiar with the os then you can dual boot xp and linux and then switch to linux if you feel really confortable with it. at the beginning i did not know what was going on with linux. but installed it as a dual boot, and now i find myself using linux like 80% of the time.

---

### Post by PryGuy on 2006-01-04
Well, I don't know as for VMWare but it works bloooody slow in VirtualPC! But maybe one should thank M$ for that... ;)

---

### Post by pbb on 2006-01-04
Yeah that is a known problem. For some weird reason, Microsoft doesn't seem to like people running Linux using their software, can you imagine that??
VMWare is lots better to run Linux, I've been doing it for some time also. And, even better, by the time you're ready to switch to Linux, you can install VMWare on Linux, and run Windows XP inside VMWare!

---

### Post by kingsidy on 2006-01-04
ms virtual pc suck and has issues with free ram from my experience. Vmware is much much faster and easier to set up

---

### Post by Generic1234 on 2006-02-04
just thought i'd post to this thread again, to let you all know:  i installed ubuntu (well, kubuntu to be exact) again a couple of days ago.  this time i worked out how to set up my internet connection on it, so ill probably be sticking with it.

---

### Post by wanger123 on 2006-02-05
Good stuff Generic, welcome back. I have been using linux for about 18 months, and ubuntu/kubuntu for more than 12 months and I love it! I completely removed window$ just before Christmas for good :mrgreen: 

wanger

---

### Post by handy on 2006-02-05
Dual booting has to be the most comfortable & reassuring way to make the change.  

When it suits you, you dabble in Ubuntu a bit more, talk to the forum with questions when needs be, before you know it you hardly ever boot windoze... :KS

How can you leave us?  We will do anything for you!  We care! :mrgreen:

---

### Post by sunny_nwho on 2006-02-05
I would strongly recommend reinstalling Ubuntu and try it...as others said...if u ever want to get into linux again then this is the time go for it my friend....I completely removed windows and entirely running on ubuntu on my laptop and it works like a charm and i can do everything I can do on Windows...and it is more safe and secure too....no virus, spyware, and all the M$ bullshit...Anyway the decision is upto u....but if u do have problems with Ubuntu...this forum is always there for u to discuss.....Sunny

---

### Post by jakethesnake on 2006-11-06
This may sound like a totally dumb question but can anybody give me an quick short summary of the difference between unbuntu and kubuntu is?

---

### Post by phersotty on 2006-11-06
> **jakethesnake said:**
> This may sound like a totally dumb question but can anybody give me an quick short summary of the difference between unbuntu and kubuntu is?

The most obvious is ubuntu uses gnome and kubuntu uses kde.  You can have them both on the same system.  Its more of a preference thing and each environment has a little different set of programs to choose from.

In future posts you might want to post a new thread or in a current conversation since the date on this thread is from February.  It just might noticed quicker.

---

### Post by jakethesnake on 2006-11-06
I know I saw that and realized the fact after I posted. Sorry for the well.. late reply. :-#

---

### Post by madfella on 2007-11-20
Ok, so I installed Ubuntu 7.10 about a week ago on my Inspiron 1521 with a Sigma Tel HD Audio controller and a Dell Wireless 1490 Dual Band WLAN Minicard...and...no sound or wireless connectivity. I've searched high and low for a fix to no avail. I'm trying to learn but getting frustrated. I thought I could do it because I use RedHat at work...uhhh no. Anyhow, just today I Googled "Remove Ubuntu" and came across this thread. Do any of you know how I can fix this?

---

### Post by PryGuy on 2007-12-21
Can't help you, sorry... :( But hey, I'm sure these problems can be solved! Sorry to hear that 'cause I'm a system administrator and I install Ubuntu on clients' PCs and I have to tell you that I had a 'no sound problem' on desktop PCs twice only and I've got about a 100 PCs converted so far. Notebooks is a harder task, I had a problem with ATI video on a notebook once. It's hard to imagine but it didn't have the Vesa mode so I had to install the video card driver in text mode. But it's so ATI so I don't bother... :) 

You better search this forum instead of googling! People here are really helpful! Good luck!

---

