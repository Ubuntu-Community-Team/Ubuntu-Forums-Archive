---
title: "64-bit not recommended for daily desktop usage - Why ??"
date: 2010-06-20
forum: Desktop Environments
---

### Post by expatCanuck on 2010-06-20
Greetings -

New to Ubuntu.
Was wondering ... why the disclaimer re: the 64-bit desktop not being recommended for daily desktop usage??
Thanks.
 - Richard

---

### Post by sanderd17 on 2010-06-20
Most apps are exhaustively tested for 32 bit and some just don't have a 64 bit package. If you are a normal desktop user, you don't need the little bit extra 64 bit gives you.

I use 64 bit as a quite normal desktop user and since version 8.10 I didn't have any problems with it but I don't feel a real speed difference if I compare it to the 32 bit variant I tried.

---

### Post by clrg on 2010-06-20
There might be no 64bit-versions of certain programs. 

I've used 64bit versions of Ubuntu for three years now and I've never encountered any problems. I think, the only real advantage of 64bit is the ability to address more than 4096 MB of memory. 

So in conclusion, if you have  + || = 4GB of RAM, go with 64bit. If not, it doesn't really matter.

---

### Post by earthpigg on 2010-06-20
> **clrg said:**
> if you have  + || = 4GB of RAM, go with 64bit. If not, it doesn't really matter.

no longer true :D

```
[chris: ~]$ free -m
             total       used       free     shared    buffers     cached
Mem:          **_6035_**       2696       3338          0        151       1788
-/+ buffers/cache:        756       5279
Swap:            0          0          0
[chris: ~]$ uname -a
Linux chris-desktop 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 _**i686**_ GNU/Linux
[chris: ~]$ 

```

problems i've had using 64-bit, spread across Ubuntu 9.04, 9.10, and Arch Linux:

-32 bit flash works better. problem relating to this - hulu.

-games. world of goo, defcon, and a few other linux-native games, are 32-bit only. 

-new software in general. the newer it is, the less likely the 64-bit version is to be as stable as the 32-bit version. the generalization is especially true if you choose to use proprietary software.

---

### Post by clrg on 2010-06-21
PAE is a workaround, not a solution. In three years, when our workstations will have 32GB of RAM, you'll need 64bit.

---

### Post by quirkification on 2010-06-21
I believe the game Scorched Eater 3D only works on 32 bit. I run 64 Bit and that game made me crash, on all setting. I had to do Force Shutdowns #-o

On a side note, isn't 64 bit kind of a flop anyways...does it really make anything run more efficiently or is it simply just more difficult to get things to run with it? ):P

---

### Post by danzvash on 2010-06-21
Interesting - I had not seen 32bit version being recommended before by Ubuntu, and it makes the advice offered at odds with the advice here: [https://help.ubuntu.com/community/32bit_and_64bit#What should I choose - 32 or 64 bit?]("https://help.ubuntu.com/community/32bit_and_64bit#What should I choose - 32 or 64 bit?")

I guess the main reason that 64bit is NOT recommended now, is that the general desktop user is very dependent on Adobe Flash for a huge proportion of websites. (Please, oh please, let an open, public standard replace this dependency soon!)
I have been using the alpha version of the 64bit Adobe Flash player since it was released (version 10.0.45.2) without many issues (CPU usage is a bit high though) ....

But just recently, in the last week or so, I have noticed a lot of instability with the 64bit Flash player in both Firefox and Chrome, with the message 
```
Gdk-WARNING **: XID collision, trouble ahead
```
visible if run from the console.
Strange how this seemed to coincide with Adobe (supposedly temporarily) dropping 64bit support for Flash on Linux .... 

So, it seems that as there is negligible performance difference between 32bit/64bit except in very specialized situations, you are going to have MUCH less trouble running 32bit rather than 64bit. As other people in this thread have stated, there are numerous examples of apps that are problematic (or even non-existent) in 64bit compared to 32bit.

---

### Post by coskierken on 2010-06-22
My take, after using 64 and 32 bit versions.  At first, 64-bit was not stable and crashed a bit.  Now, it is steady as a rock.  64-bit is written clean.  I have a laptop with 1.5Gigs of ram and it runs great with 64-bit.  The resource usage is low.  As for normal desktop use, there is no reason not to run it.  I don't know what problems people are having with Adobe, but I have none at all now.  Sure, a while back, it had problems, but not now, as far as I am concerned.  If you want to run a 32-bit game, install the 32-bit library.  Just look it up and see how to do it.  Or, dual-boot with Win7 (I do just for games) to play.  The main reason I use 64-bit on my desktop (C2Q Intel@3.4G with 8G ram) is to crack movies to a library.  I did a test on a normal DVD of about 1.5 hours. and it took only 16 minutes with Handbrake which will use all the cores on a multi-core processor.  If you are using any cpu intensive app and can get the 64-bit version of a program, use the 64-bit OS.  You won't regret it.

---

### Post by bhishan on 2010-06-22
I have been using 64-bit since 9.10, the only problem I have is with flash sometimes. When I used to use 32-bit I used to have some problem with flash too. So, I think for regular desktop users 64-bit is fine. If more people start using it then only the developers will start making software with 64-bit in their mind.

64-bit rocks:guitar:

---

### Post by XSAlliN on 2010-06-22
> **expatCanuck said:**
> Greetings -

New to Ubuntu.
Was wondering ... why the disclaimer re: the 64-bit desktop not being recommended for daily desktop usage??
Thanks.
 - Richard

They keep copying this line with any new release, since 32 bit is less buggy cause of the reasons mentioned above. So less buggy, means more stable - and that's what they recommend. With 32 bit simply works, yet with 64 bit you might need some workarounds, extra work for some things - which is not beginners friendly. And probably there are many in this situation - even you from what you mentioned - so you might be better of with 32 version...

---

### Post by cascade9 on 2010-06-22
> **earthpigg said:**
> -games. world of goo, defcon, and a few other linux-native games, are 32-bit only. 


WorldOfGoo might be 32bit native, but works fine in 64bit for me with dkpg -i --force-architechture****.

---

### Post by XSAlliN on 2010-06-22
> **cascade9 said:**
> WorldOfGoo might be 32bit native, but works fine in 64bit for me with dkpg -i --force-architechture****.

That option is like rape for people with strong ethics, so guess 32 bit is still a better option for some.

---

### Post by earthpigg on 2010-06-22
> **cascade9 said:**
> WorldOfGoo might be 32bit native, but works fine in 64bit for me with dkpg -i --force-architechture****.

there is a [much more elegant solution]("http://2dboy.com/forum/index.php?topic=1464.0") to playing World of Goo on 32-bit systems. one that does not require you to ram large objects down your computer's throat.

edit: [corresponding ubuntuforums thread ]("http://ubuntuforums.org/showthread.php?t=1070885")

---

### Post by oldos2er on 2010-06-22
The "not recommended for daily use" phrase only appeared after 10.04 was released; it didn't exist previously. Canonical has been silent on its meaning, AFAIK.

[https://bugs.launchpad.net/ubuntu-website/+bug/585940](https://bugs.launchpad.net/ubuntu-website/+bug/585940)

Note the 64-bit subforum here was closed last year because of "... the fact that 64 bit Ubuntu has matured and there are very few 64 bit specific issues." FWIW.

---

### Post by danzvash on 2010-06-24
I've just noticed [this performance comparison]("http://www.phoronix.com/vr.php?view=14477") between 32-bit and 64-bit that the Phoronix guys did 6 months ago.

The performance increases are generally between 50 - 1000 % (!) between 32bit and 64bit.

It's a convincing argument for sticking with 64bit - and now that I've started using the [64bit Flash PPA, ]("https://help.ubuntu.com/community/RestrictedFormats/Flash#Ubuntu 9.10 (Karmic Koala) and later") those Flash issues are less noticeable somehow ....

---

### Post by MGSteve on 2010-10-02
Any performance gains are ONLY there if you run purely 64bit software, otherwise you're running 32bit software on 64bit OS. The real benefit is using RAM more than 4GB.

Which brings me to the following. I'm currently running W7 x64 on my PC and am considering reinstalling it in the next month or so as a need to reflash the SSD drives I've got in the RAID and as they're the main OS drives, I want to wait until I reinstall the OS anyway to do it. W7 has been far more reliable than any other version of windows, although plugging a TomTom into it does appear to cause a blue screen when I run TomTom home!

Anyway, gripes aside. As I have 12GB of Ram I obviously need a 64bit OS. Now, the question is with windows you can run 32bit software without a problem, is this the same with Ubuntu? As I keep reading that a main detractor of 64bit is lack of flash support. Now, surely the easiest option would be to install a 32bit version of Firefox / Chrome / whatever, along with the 32bit version of Flash. Because this isn't suggested, it seems to imply that any software you install on a 64bit build of Ubuntu has to be 64bit itself?

Can you confirm this is the case or not as it will mean I stick with W7 if that's the case.

---

### Post by formaldehyde_spoon on 2010-10-10
> **quirkification said:**
> I believe the game Scorched Eater 3D only works on 32 bit. I run 64 Bit and that game made me crash, on all setting. I had to do Force Shutdowns #-o

On a side note, isn't 64 bit kind of a flop anyways...does it really make anything run more efficiently or is it simply just more difficult to get things to run with it? ):P
Yes, it really *can* be more efficient, and therefore faster - as long as the binaries you use are compiled on 64 bit.

It's no more difficult to get things to run on it than 32 bit.

For those looking for the new 64 bit Flash: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

@OP: mainly because some people don't know what version their hardware supports, so 32 bit is a 'default' that will work with 32 and 64 bit hardware.

---

### Post by varnav on 2012-08-19
While download page recommends 32 bit, Wiki says the opposite:

*Unless you have specific reasons to choose 32-bit, we recommend 64-bit to utilise the full capacity of your hardware.*

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by Deepak J on 2012-08-19
The advantages of 64-bit are better memory handling when mem size>4GB, better video rendering capabilities(when the video quality is HD, Blu-ray or 3-D).

---

### Post by Deepak J on 2012-08-19
Also this thread might help you:

[http://ubuntuforums.org/showthread.php?t=1494755](http://ubuntuforums.org/showthread.php?t=1494755)

---

### Post by overdrank on 2012-08-19
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

