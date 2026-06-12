---
title: "HELP! Want Ubuntu for Dell Inspiron Mini12"
date: 2009-09-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dougproudman on 2009-09-03
Hello All,

I am desperate for your help.  I love Ubuntu, but have not been able to figure out if I can get it for my Dell Inspiron Mini 12 (Inspiron 1210?).  It is a notebook, but a large one.  I got it in Japan and there they did not have the option of having Ubuntu pre-installed, so I gave in and got it with Vista Home Basic...a big mistake.  It is unbelievably slow.  I can't stand it.  

So, my questions are 1. Which Ubuntu is best for my computer?  And 2. What is the fastest way to get it.  

Once I get it installed, I hope to never look at another Vista OS again! 

Peace,
Doug

---

### Post by mikewhatever on 2009-09-03
Download the desktop 9.04 iso and use [Unetbootin]("http://unetbootin.sourceforge.net/") to put it on a USB stick. Then follow any of the installation guides.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

9.04 doesn't include the driver for gma500, so that, once installed, you'll have wrong resolution and relatively slow performance. Use the following to apply a fix. [http://ubuntuforums.org/showthread.php?t=1213416](http://ubuntuforums.org/showthread.php?t=1213416)

---

### Post by dougproudman on 2009-09-03
Dear Mikewhatever,

Thanks very much for your help!  One last question to you.  Will this only give me an option to run the Ubuntu OS, or will I also have a chance to get rid of Vista altogether if I want to?

Thanks,
Doug

---

### Post by mikewhatever on 2009-09-03
You can either install Ubuntu side by side with Vista, or format the entire HDD and have Ubuntu only.

---

### Post by vttay03 on 2009-09-03
Unfortunately, Vista doesn't play well as a dual boot system if you were to strictly set it up from the Ubuntu Live CD installer.  If you really wanted the dual boot configuration with Vista, you'd have to shrink the size of the Vista partition within Windows before installing Ubuntu.  However, the smart thing to do (which you seem to have already figured out) is to just do the full install and blow Vista away completely.

---

### Post by dougproudman on 2009-09-06
Hi Again, Mikewhatever,

Thanks again for your help.  Alas, I have yet another question...it's about the driver for gma500.  The truth is, I know very little about computers and programming, so if I have to do things that are too complicated for me with Ubuntu, I might give up.  Anyway, as you said, if I install the OS, I will need to install the driver for gma500.  Is the thread you lead me to the easiest way to do that?  Is there an even easier, super-easy way to do that for computer idiots like myself?  I want Ubuntu for it's simplicity and to escape from the progressively slow and greedy Microsoft OS, but I'm not sure if I am up to the technical challenges.  Any help? 

Thanks,
Doug

---

### Post by mikewhatever on 2009-09-07
Yes, there is an easier way, if you don't mind using Ubuntu 8.04. GMA500 should be working out of the box with a correct resolution. I am quite sure why I hadn't suggested it before, given the complicated procedure of dealing with gma500 in Jaunty.
8.04 is a long term support release, pretty solid and well maintained.

---

### Post by Montala on 2009-09-07
If I can just 'jump in' on this one, do we know yet whether the GMA500 will be fully supported, and working 'out of the box' under Karmic?
 
I am assuming that it will be under the Netbook Remix version also?

---

### Post by mikewhatever on 2009-09-07
No, not unless something changes before 9.10 is released. It looks like we are stuck with Hardy Heron only working out of the box,or else the hackery linked too.
[http://www.phoronix.com/scan.php?page=news_item&px=NzQzMg](http://www.phoronix.com/scan.php?page=news_item&px=NzQzMg)

---

### Post by Montala on 2009-09-07
Oh dear... that is a shame!
 
It looks as if Intel is hoping that Ubuntu (and other) Linux users will switch to Moblin then! :(

---

### Post by mikewhatever on 2009-09-07
> **Montala said:**
> Oh dear... that is a shame!
 
It looks as if Intel is hoping that Ubuntu (and other) Linux users will switch to Moblin then! :(

Moblin would be nice, but the thing is, it doesn't have gma500 support either according to its Known Issues page. GMA500 was supposed to be a gpu for MID devices, so that I don't quite understand why.

[http://moblin.org/documentation/test-drive-moblin/known-issues](http://moblin.org/documentation/test-drive-moblin/known-issues)
> Platforms with the GMA-500 Graphics chipset are not supported.

You might want to tell Dell what you think about gma500 on ideastorm.com:
[http://www.ideastorm.com/ideaView?id=087700000000X1AAAU](http://www.ideastorm.com/ideaView?id=087700000000X1AAAU)
[http://www.ideastorm.com/ideaView?id=087700000000QzAAAU](http://www.ideastorm.com/ideaView?id=087700000000QzAAAU)

---

### Post by dougproudman on 2009-09-07
Hi Mikewhatever,

Thanks so much for your response (and also for MONTALA 'jumping in'. Anytime!).
So, just to clarify, I can download the Ubuntu 8.04 OS onto a 1 gb (minimum) USB and install that.  Also, does a netbook remix exist for that release?

I'm sorry for all these basic questions.  Please feel free to ignore me!  :-)

Kindly,
Doug

---

### Post by mikewhatever on 2009-09-08
I don't think 8.04 UNR is available as an image file for download, but the UNR related files can be installed once the desktop version is in place. There isn't really a need for UNR's interface, given the bigger screen and resolution of the Dell mini 12, but that is up to you. [Read here for more.]("https://wiki.edubuntu.org/UNR/Installation/Hard")
What you need to do to install from USB is: download the 8.04 iso to your Vista partition, use Unetbootin to place the iso on the USB drive, and then boot from the USB drive.
You seem to be correct about the minimum size of the flash drive.

---

### Post by dougproudman on 2009-09-09
MikeWhatever,  
 
Thanks again for all your help!   I will give this a shot and not go with a UNR.  
 
Peace,
Doug

---

