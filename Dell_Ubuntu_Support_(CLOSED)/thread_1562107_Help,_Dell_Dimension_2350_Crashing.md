---
title: "Help, Dell Dimension 2350 Crashing"
date: 2010-08-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by portsmouth7 on 2010-08-27
I am very new to this forum so please forgive me if there is an answer to this somewhere else, but I couldn't see one.
 
I have a problem, I have installed Ubuntu 10.04 on my Dell Dimension 2350. The machine has a 30G hard drive, 750 mb ram and an Intel Celeron 2.0 Processor. In view of the spec of the machine, I didn't want to install Microsofts latest money making racket on it but I really like Ubuntu. I previously had Windows XP on it which refused to go past the boot screen after 8 years of using it.
 
I retreived documents from hard drive, and installed Ubuntu, which I believed erased Windows XP (whic is fine by me.)
 
Ubuntu is running fine, but occasionally it crashes. The symptoms are that the screen slowly goes blank which cannot be rectified even when I move the mouse. THen I can see vertical Zebra stripe type lines from half way up the screen to the top, intermittently flashing in the background. Aafter restarting, it goes, but this happens about 4 or 5 times a day.
 
Is there a driver or add on that I need to download or install, what do you recommend? Is it perhaps the version that I am using. Should I install an earlier version instead?
 
I look forward to your answer. 
 
Regards
 
David Walker.

---

### Post by Baji P. on 2010-08-27
I would say your laptop specs are pretty reasonable except perhaps the memory, which is just a little bit on the lower side.

If your machine is crashing 4 or 5 times a day, I would not call that occasionally.

There could be a couple things happening here, you may not have selected all repositories which could be blocking you from taking advantage of proprietary drivers that can resolve this issue. Secondly, your kernel may have been installed with all drivers causing it to be excessively bloated.

My suggestion, burn a 10.04.1 Alternate CD, reinstall with that, when you reinstall, after selecting your language, hit F6 and choose "Expert Install", this will take you step by step through the install. In most cases the default selections will be fine.

When you are asked about different package repositories, make sure you select all of them including  Backported  software. When you are asked to select if the target kernel should include all available drivers or only drivers needed for this system, choose the latter.

Good luck !

-baji.

---

### Post by mörgæs on 2010-08-27
Agree on the post above, but before reinstalling please post the output of 

```
hwinfo --gfxcard
```

If you reinstall, remember to have wired internet access while installing.

---

### Post by Rachel5000 on 2010-08-29
[FONT=Book Antiqua][SIZE=2][COLOR=Red][B]portsmouth7: 
I think I'm having THE SAME PROBLEM. And I have the same system. I'. posting my opening thread below. Have you gotten this resolved? Please forgive the red and the yelling. I'm just excited is all :P
Thanks,
Rachel
[/B][/COLOR][/SIZE][/FONT] 			 		   		 		 		
[http://ubuntuforums.org/showthread.php?t=1563275](http://ubuntuforums.org/showthread.php?t=1563275)

Hello,
I am a new user - I did a full install of Ubuntu 10.04LTS 5 days ago.[COLOR=Red]** On  a Dell Diminsion 2350**[/COLOR]. The reason was: I Hate Windows and there's just  got to be a better way, so I got a hard copy and installed it. Here's  what's happening: The whole thing just locks up.[B][COLOR=Red] I get a message and  then the screen will flash something that looks like piano keys across  screen. Here's the message (Always the same)
[/COLOR][/B]  
***Speech-dispatcher configured for user sessions (OK)**
***Starting common Unix Printing System: cupsd**
***PulseAudio configured for per-user sessions**
**Enabling Additional Executable**
**Binary Formats binfmt-support**
**Checking Battery State**
**(OK)**
 
As I attempted to repair this on the advise of others, I changed out the  monitor - Someone said it was an **Nvidia Driver** that needed to be  removed or disabled, so change monitor first. Another person said to  re-format, so I did. Yesterday. It's still happenig, and with greater  frequency. There are a few other problems, but this is the worst. When  this happens the only remedy is to shut off power. One more thing - This  problem usually happens when OS is executing a command - Starting  Firefox, Opening Office or Movie Player. Or, it happens as soon as  desktop loads. 
 
Sorry if I'm a bit convoluted here - I just found out about Linux/Ubuntu  a few weeks ago and have NO CLUE what I'm doing. If anyone knows how to  repair this, they are more than welcome to connect remotely and do so. -  I cannot pay as I am included in "The Poor" Robin Hood was going on  about...

---

### Post by portsmouth7 on 2010-08-31
Hi Baji

Thanks for that info, I appreciate it. I will get on to that and see if it works.

Dave

---

### Post by portsmouth7 on 2010-08-31
Hi Baji P
 
I burned a new version of Ubuntu 10.04.1 and tried to install it. But after selecting the language, I hit F6 but did not get any menu or selection coming up anywhere. It just went straight on to the world map for me to choose the time zone. So I thought I would come back here before proceeding (thankfully I can access this forum on my second machine.)
 
Is there anywhere else within an installed version of Ubuntu that I can select or deselect those drivers or perform those functions that you have mentioned? Because I cannot see where to do it in the install process.
 
I look forward to your reply, thanks for your time.
 
Dave

---

### Post by portsmouth7 on 2010-08-31
Hang on, wait I have just realised that it wasn't the "alternate" ISO file that I downloaded but the same one as before.
 
I'll do the alternate one as you have suggested and see what happens, then I'll let you know.
 
Sorry for my mistake
 
Dave

---

### Post by portsmouth7 on 2010-09-02
Hi Baji P
 
I have tried the alternate version of Ubuntu but I find the menu choices a little confusing, I don't want to make wrong selections at critical stages which may impair the performance etc.
 
Is there a walk through tutorial of the Ubuntu alternate CD?

What about Xubuntu or Kubuntu, would one of those be less likely to crash perhaps?

Dave

---

### Post by portsmouth7 on 2010-10-02
Hi

Its still crashing. Someone told me to insert    i915.modeset=1     after the but that says "quiet splash" in the grub menu every time I start Ubuntu. I have been doing but it still crashes about twice a day.

Dave

---

### Post by mörgæs on 2010-10-02
Have you tried 9.10 or 10.10?

---

### Post by portsmouth7 on 2010-10-04
Hi, I didnt realise that 10.10 was out but I might give that a go. Failing that I may try 9.10 or earlier.

Regards

Dave

---

### Post by garethfoxwilliams on 2010-11-09
I have a very similar problem

My parents' ( they are 80 and 78 y/o ) Dell Dimension 2350  has been  running WinXP for years. 

It has the Intel845G chipset with Intel  Integrated 3D Extreme Graphics.

As I have just got them onto broadband, I have clean installed 10.04 Lucid, which they like.

During the post-install upgrade, there was a graphics crash ( I assume)    giving slightly slanted black/white stripes all across the screen and  an unresponsive computer this   persisted after an immediate restart, so  I re-installed immediately.

Now, suddenly, several weeks later, they are experiencing similar crashes on an occasional basis. 

Apparently things are sometimes OK after a restart, but recently, it was still bad after several restarts.

The next day, things were fine for a while and crashed later. I think crashes are now more frequent.

Sadly, they live several hours drive from me and so I can't get access    to the machine till December. However I'm looking for clues in the    meantime, or an easy fix I can talk them through - any ideas?

---

### Post by mörgæs on 2010-11-09
Intel 845 and Ubuntu 10.04 didn't really get along:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

There are some good workarounds in that thread, but I don't know if you can remote control your parents... 

Else a clean install of 10.10 is worth trying, if you send them an install disk. If you are in the phone meanwhile I guess they should manage.

---

### Post by garethfoxwilliams on 2010-11-10
Thanks.

All replies and research points towards a clean install of 10.10 being the best option, which I can do for them in a month's time.

Cheers

---

