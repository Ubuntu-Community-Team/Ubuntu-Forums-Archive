---
title: "--10 QUESTIONS seeking ANSWERS--"
date: 2009-03-27
forum: General Help
---

### Post by gorucan on 2009-03-27
[B][COLOR="DarkRed"]Hello everyone,
I am 17 years old and I don't know much about computing so I would really appreciate any help. I collected 10 questions I really need solved. I'd kindly ask you to answer as simply as possible as my english isn't my native language and I am also new to linunx and unix stuff. :)[/COLOR][/B]

**Question Nr. 1**

I really like Ubuntu, I just got used of it, but I like to test other OS-es also, so few days ago I decided to try FreeBSD, I managed to get it installed on my old external 80gb disk and it worked, but I just couldn't set it up to connect to the internet although i was reading FAQs and it just didn't work. Well then i decided I should start with easy way- PC-BSD.


The problem is following... I have those partitions:

-8 GiB (with Win XP on it) - primary

-one 100 GiB primary partition split to two partitions: 70 GiB of NTFS (windows 7 on it) and 30 GiB of ext3 (empty)

-one 4 GiB linux swap (which doesn't work as it should, more about that later)

-one 40 GiB primary partition with ext3 and Ubuntu 8.10 on it

The PC-BSD setup only detects the 8-GiB partition with XP which I would really never want to delete, it also shows the 4-GiB swap and 40-GiB one with Ubuntu... I used gparted live cd and shrinked my NTFS 100-GiG partition to 70-GiG as you can see above and the rest 30 GiB i formatted to ext3, just didn't know what format BSD will use so i took ext3... And none of last mentioned (70 and 30) are listed there on installation interface :(
So what should i actually do??? **I want BSD on the 30-GiB partition and It's not primary one so i think that's the reason it won't detect it...** In Gparted it doesn't allow me to change it to primary, I tried deleting it and changing it to primary but option is unclickable - not possible. Help please !


**Question Nr. 2**

This one is about windows... I know you guys don't like it and you use Wine to run win programs but anway, here is my question and I hope someone could help me. 

I installed CCleaner on Windows 7 and did registry cleanup.
I thought this would make it run smoothier but all i achieved was all dialogue windows' buttons had no text on them ! So i thought system restore could handle that and I ran the only restore point I had... Even worse... buttons work now but I am completely unable to use minimise-maximize-close buttons, I can't resize them... They are there, but when i click them nothing happens... I have to quit apps with alt+f4 or taskbar-right click-close...
I know the solution would be to load the original windows 7 registry over my current registry and then it would be like new... I installed windows with mounted iso through win XP so I can't use disc to reinstall it and I also don't want to reinstall it just because of registry... Now, the question: **Does anyone where I could download complete windows 7 regirsty for build 7000?**


**Question Nr. 3**

When I lock screen in Ubuntu, It prompts me with login screen where I have to enter password to go back in. Same goes with stand-by. Now there is this **damn little picture of flowers**, like on windows users where you have those frogs, chess, cats... I was searching settings for this icon but I can't see where I could change it !! I want to change it to something else than flowers or at least get rid of it. Anyone has a solution?


**Question Nr. 4**

When i try to Hibernate my Ubuntu,** goes all black first then white text on black screen reports some kind of failure** for just a second then it's black again and it hangs and sometimes it turns off completely instead of going to hibernate and sometimes it hangs and i have to hold power button to shut down the laptop :( ... Computer is Dell laptop inspiron 1720 with intel core 2 duo 2,2 ghz with 2 GiB ram and i use 4 gb swap partition and graphics card is GeForce 8600M GT... any idea why this happens?
I must use Stand-by all the time instead of hibernation...


**Question Nr. 5**

This is a big thing. I have one old HP laptop compaq nx9005
from year 2003... (AMD 2400+ 512ram) Around 2 years ago when it was my only laptop i was using it with Windows XP all the time, had happy time with it and the main reason for what i will soon explain was probably that I didn't turn it off for months, i kept it running with torrent and e-mule day and night, and even when i turned it off, i just put it on stand by. One day it was all working fine until I installed Bugzilla and after install it asked me to restart computer... it didn't load anymore. Bios worked still but it didn't want to boot windows. I gave the computer to one geek who made it work again. I thought I'd give it to my mother and I used it for a week or so, and after first 5 startups bios was all slower.. then after 5th boot it  sometimes hanged on bios and sometimes hanged while windows was loading and sometimes it just turned itself off while i was working. I realised this i better move the data to extern disk because I gave up with that laptop.
Now it's in this state: when i turn it off, bios logo shows up and F2 option for setup F12 for lan boot and ESC to change boot order. And there it hangs... forever. When i try to enter bios setup, it takes up to 10 minutes to show it up but the setup works flawlessly after I'm in. If i want to change boot order, it takes around 5 minutes too and then i wanted to run ubuntu 8.04 live cd to rescue my valuable data to an extern disk or SD cards, it kept trying to do something, ventilation goes on max, computer hot as hell... And then after 10 minutes, turns itself off and reboots automatically... Only thing i could do to stop the 10-min rebooting is hold power button and turn it off manually...
**Now, I need that data on hard disk badly...** I think there is something wrong with motherboard?? So should i take disk out of laptop and put it in some other computer? Will it fit in any other computer or i need to find same architecture???


**Question Nr. 6**

In Ubuntu 8.10 if I press ctrl+alt+F2 it opens the command line interface, i log in as root (yes i have it enabled, sorry) and then after i'm done for example I want to shut down the computer with *shutdown now* or in terminal in GUI _sudo shutdown now_ i get the same result... It starts shutting down and the graphical ubuntu logo with the orange loader goes to the end and there is just a little bit left until it should be turned off, **then it hangs** untill i hold power button to turn it off... Why that???


**Question Nr. 7**

About performance... Does compiz slow my startup a lot? Because XP loads even faster than ubuntu... Maybe I have too many effects  and startup items enabled? (dock, screenlet-sys monitor, many compiz effects) Of course after it stops loading it works just fine but still some apps need too long to start up... 
I would also like to remove the ubuntu logo when i boot the OS, i don't want to see that loader, **how do i remove it??**
And a subquestion, **where is the boot order file** where i could reorder boot list?


**Question Nr. 8**

Once I manage to have Ubuntu and BSD both installed on this same laptop, is it okay to allow **both OS-es to use same swap partition???** 


**Question Nr. 9**

I would like to set up a home server, and i was thinking of Ubuntu 8.10 server edition for it. **I would like it to be FTP server where i would have password access through browsers to download my files...** Now there are subquestions:
-I don't know anything about setting up a server. Is there any kind free lesson how to do it? Is it complicated to do it on Ubuntu? (Ubuntu- linux for people...?)
-If i get box with 2,4 ghz 1-core intel pentium 4, 1 gig ram, 1000 GiB disk and internet VDSL with 4mbit download and 1 mbit upload, will this work fine if i share contents of server with max of 3-5 people? (i can't afford better hardware right now)


**Question Nr. 10**
All those things i am doing on my Dell laptop... Is there any risk for my HDD to break because I move partitions and experiment and format it all the time? Will it survive all this stuff or do I better do this on a desktop... which is not fine option for me, i travel a lot :s


**Thanks for any help and sorry for soooo long post :)**

---

### Post by gorucan on 2009-03-27
bump

---

### Post by overdrank on 2009-03-27
> **gorucan said:**
> bump

Please do not bump so quickly as it is rude and also it would take longer than that for some one to reply to 10 questions. :)

---

### Post by gorucan on 2009-03-27
> **overdrank said:**
> Please do not bump so quickly as it is rude and also it would take longer than that for some one to reply to 10 questions. :)

Sorry. I was used of some really-really quickly moving forum (doesn't matter what one now) But all 10 questions don't need to be answered from same person or in same post :)

---

### Post by sv1cdn on 2009-03-27
> Question Nr. 3

When I lock screen in Ubuntu, It prompts me with login screen where I have to enter password to go back in. Same goes with stand-by. Now there is this damn little picture of flowers, like on windows users where you have those frogs, chess, cats... I was searching settings for this icon but I can't see where I could change it !! I want to change it to something else than flowers or at least get rid of it. Anyone has a solution?

Go to System>Administration>Login window then tab local. This should do the job. Do not forget to enter root password! Can't do otherwise.

---

### Post by sv1cdn on 2009-03-27
> 
Question Nr. 4

When i try to Hibernate my Ubuntu, goes all black first then white text on black screen reports some kind of failure for just a second then it's black again and it hangs and sometimes it turns off completely instead of going to hibernate and sometimes it hangs and i have to hold power button to shut down the laptop ... Computer is Dell laptop inspiron 1720 with intel core 2 duo 2,2 ghz with 2 GiB ram and i use 4 gb swap partition and graphics card is GeForce 8600M GT... any idea why this happens?
I must use Stand-by all the time instead of hibernation...

This one is a bit more complicated. I believe problem comes from Nvidia drivers, even Ubuntu nvidia drivers! Follow up this:

[http://ubuntuforums.org/showthread.php?t=79295](http://ubuntuforums.org/showthread.php?t=79295)

but mistakes can very well crash your Ubuntu installation! Easier solution, disable nvidia driver from:

System>Administration>Hardware drivers

---

### Post by sv1cdn on 2009-03-27
> Question Nr. 5
Now, I need that data on hard disk badly... I think there is something wrong with motherboard?? So should i take disk out of laptop and put it in some other computer? Will it fit in any other computer or i need to find same architecture???


I have heard that you can find in computer shops special kind of adapters for laptop hard disks which you can install in your desktop and have the hard disk mounted.

---

### Post by sv1cdn on 2009-03-27
> Question Nr. 6

In Ubuntu 8.10 if I press ctrl+alt+F2 it opens the command line interface, i log in as root (yes i have it enabled, sorry) and then after i'm done for example I want to shut down the computer with shutdown now or in terminal in GUI sudo shutdown now i get the same result... It starts shutting down and the graphical ubuntu logo with the orange loader goes to the end and there is just a little bit left until it should be turned off, then it hangs untill i hold power button to turn it off... Why that???

This happens in my old pentium 3 pc with Ubuntu 8.10 I believe this has something to do with acpi support and compatibility of motherboard to Ubuntu. If you shutdown from graphical user interface you get the same response? If yes then acpi could be the problem.

---

### Post by sv1cdn on 2009-03-27
> Question Nr. 7

About performance... Does compiz slow my startup a lot? Because XP loads even faster than ubuntu... Maybe I have too many effects and startup items enabled? (dock, screenlet-sys monitor, many compiz effects) Of course after it stops loading it works just fine but still some apps need too long to start up...
I would also like to remove the ubuntu logo when i boot the OS, i don't want to see that loader, how do i remove it??
And a subquestion, where is the boot order file where i could reorder boot list?


Boot order comes from bios of motherboard, haven't seen it else.
Compiz does slow a lot! Disable it at:

System>Preferences>Appearance>Visual Effects set it to none.

---

### Post by sv1cdn on 2009-03-27
> Question Nr. 9

I would like to set up a home server, and i was thinking of Ubuntu 8.10 server edition for it. I would like it to be FTP server where i would have password access through browsers to download my files... Now there are subquestions:
-I don't know anything about setting up a server. Is there any kind free lesson how to do it? Is it complicated to do it on Ubuntu? (Ubuntu- linux for people...?)
-If i get box with 2,4 ghz 1-core intel pentium 4, 1 gig ram, 1000 GiB disk and internet VDSL with 4mbit download and 1 mbit upload, will this work fine if i share contents of server with max of 3-5 people? (i can't afford better hardware right now)


Check this out:

[http://ubuntuforums.org/showthread.php?p=429783#post429783](http://ubuntuforums.org/showthread.php?p=429783#post429783)

---

### Post by lovinglinux on 2009-03-27
1 - I'm not a partition expert, but I think you can change it to primary using PartitioMagic under Windows (it can handle ext3). I remember I had a similar problem when I was using Windows and I solved it with this software. The only problem is that PartitionMagic is not free.

---

### Post by gorucan on 2009-03-27
> **sv1cdn said:**
> Go to System>Administration>Login window then tab local. This should do the job. Do not forget to enter root password! Can't do otherwise.
 
Thanks, solved.

---

### Post by gorucan on 2009-03-27
> **sv1cdn said:**
> This happens in my old pentium 3 pc with Ubuntu 8.10 I believe this has something to do with acpi support and compatibility of motherboard to Ubuntu. If you shutdown from graphical user interface you get the same response? If yes then acpi could be the problem.
Hmm when i shut down from GUI it works fine.

---

### Post by gorucan on 2009-03-27
> **sv1cdn said:**
> I have heard that you can find in computer shops special kind of adapters for laptop hard disks which you can install in your desktop and have the hard disk mounted.
Ok :s
Then i will need to go to shop, seems like.

---

### Post by gorucan on 2009-03-27
> **sv1cdn said:**
> This happens in my old pentium 3 pc with Ubuntu 8.10 I believe this has something to do with acpi support and compatibility of motherboard to Ubuntu. If you shutdown from graphical user interface you get the same response? If yes then acpi could be the problem.
Do you think so?
When i shut down from GUI it works just fine !!!

---

### Post by gorucan on 2009-03-27
> **sv1cdn said:**
> Boot order comes from bios of motherboard, haven't seen it else.
Compiz does slow a lot! Disable it at:

System>Preferences>Appearance>Visual Effects set it to none.
Compiz disabled, way better now.

There MUST be boot sequence file, like boot.ini on windows, i know there is one because i've seen path on some forum just i can't find it again.

---

### Post by gorucan on 2009-03-27
> **lovinglinux said:**
> 1 - I'm not a partition expert, but I think you can change it to primary using PartitioMagic under Windows (it can handle ext3). I remember I had a similar problem when I was using Windows and I solved it with this software. The only problem is that PartitionMagic is not free.
Thanks but Symantec is expensive and i dont have credit card anyway...
I need free solution... Maybe there is a tool in windows 7 integrated?

---

### Post by gorucan on 2009-03-27
bump

---

