---
title: "[SOLVED] Install Ubuntu on Dell Latitude D505"
date: 2008-06-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by poochhq on 2008-06-11
Can anyone point me to a link or thread that will take me through a step by step installation of Ubuntu on my Dell Latitude D505? I have tried v7.04 and v8.o4 but they do not seem to work very well.

Cheers,

James

---

### Post by millercn on 2008-06-11
I have a same Laptop . but I install ubuntu 8.04 have none error . I buy it in 2002.

---

### Post by overdrank on 2008-06-11
> **poochhq said:**
> Can anyone point me to a link or thread that will take me through a step by step installation of Ubuntu on my Dell Latitude D505? I have tried v7.04 and v8.o4 but they do not seem to work very well.

Cheers,

James

Hi and welcome, Could you tell us what seems to not work so well? Do you receive any errors? Does the live cd boot to the desktop? Have you check the cd and ISO for errors?

---

### Post by poochhq on 2008-06-12
My D505 had WinXP on it but then I reformatted the drive. After I run the Ubuntu CD (it doesn't matter which version) the initial Ubuntu display comes on with the different options. I choose to install Ubuntu on my hard drive. The display load the kernel and then the Ubuntu logo appears with the orange progress bar that moves left to right and back again. The progress bar then  fills up with orange and it goes to another blank screen...and then nothing happens for 30 mins- 60mins. Then I give up. The CD is still active in the tray but there is nothing else happening.

I will double check that the CD has no faults on it. When I choose the option "try Ubuntu without changing your computer" I get the same process beginning- The display load the kernel and then the Ubuntu logo appears with the orange progress bar that moves left to right and back again. The progress bar then  fills up with orange and it goes to another blank screen...and then nothing happens for 30 mins- 60mins. Then I give up. The CD is still active in the tray but there is nothing else happening! 

Many Thanks,

James

---

### Post by tpyeoh on 2008-06-12
I also encountered some problem. However, I go a bit further, it finishes the installation, and ask me to remove CD and hit return. Once I hit return, everything stops with nothing appear on the screen.

If I am confusing all of you or not elaborate well, please let me know. I jump into Ubuntu after I read this thread as a guest for a few weeks, and see so much nice thing about this.

:confused::confused:

---

### Post by satbytheriver on 2008-06-14
Well, I have the same laptop and had no problems installing ubuntu on it, just had to make some adjustments after...

Maybe it's the cd/dvd reader, i don't find it very reliable, I actually had to switch it once, though it wasn't easy...

Sorry I can't help much... good luck!

---

### Post by poochhq on 2008-06-18
Thanks, everyone. I did not have enough RAM. I upgraded it to 512MB and bingo, it works like a dream.

---

### Post by crawall on 2008-06-29
> **satbytheriver said:**
> Well, I have the same laptop and had no problems installing ubuntu on it, just had to make some adjustments after...

Maybe it's the cd/dvd reader, i don't find it very reliable, I actually had to switch it once, though it wasn't easy...

Sorry I can't help much... good luck!

could you tell me which adjustments you had to make? That would help me as newbee a lot

---

### Post by IG88 on 2008-07-14
just wondering about drivers, can I use the original drivers for windows xp?

---

### Post by aaronLund on 2011-08-28
Old thread.

I just installed 10.04 (ubuntuStudio, actually) on a Latitude d505 and had 2 problems so far:

Wouldn't boot all the way through (i.e. black screen after a couple of seconds).  Here was the fix:  [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) (workaround A)

Then, the friggin eth0 wouldn't work.  A simple 
dhclient eth0 fixed that.  

Now it's update time.  Hope this helps some other sad sack.

---

### Post by dufftime on 2012-03-04
Thanks... this sad sack is grateful. Worked great!

---

