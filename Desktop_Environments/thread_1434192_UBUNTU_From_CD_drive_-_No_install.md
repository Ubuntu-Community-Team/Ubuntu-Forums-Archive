---
title: "UBUNTU From CD drive - No install"
date: 2010-03-19
forum: Desktop Environments
---

### Post by anon_private on 2010-03-19
I have just received the UBUNTU CD.
 
When I placed it into the CDdrive I had the options to view the files or install.
 
I don't want to install UBUNTU, but I would like to run it occasionally from the CD drive.
 
How can I achieve this without replacing or affecting the Vista operating system?.
 
Thanks

---

### Post by Ozymandias_117 on 2010-03-19
Two options:

1. Insert your CD, reboot. During boot press the key your system uses for a 1-time boot menu (Usually f12 or esc most will say at the bottom or top of the screen during boot)

2. If you want to use it more often than occasionally, you may want to change your boot order in BIOS so that it looks at CDs first. During boot, press the button to get into setup (usually del or f2) again, it should say at the bottom or top of your screen during boot.

This will then allow you to boot into a "LiveCD" which lets you try ubuntu without installing it.

---

### Post by anon_private on 2010-03-20
Thanks for the response.
 
For the one-time boot option. If I use UBUNTU then finish, do I then simply close UBUNTU, remove the CD, then reboot to get back to Vista?
 
For the second option, If I boot from the CD, then I will be using UBUNTU. If I leave the CD out of the drive, I assume that I will boot into Vista. Am I correct?
 
When I read the information on the cover of the UBUNTU CD, I got the impression that I had the option of losing VISTA. Please tell me that there is no chance of removing the Vista operating system from the hard drive when using the UBUNTU CD.
 
Best wishes.
 
A

---

### Post by gordintoronto on 2010-03-20
If you click on "install Ubuntu," then do a large number of other clicks, you can wipe out Vista. It is not easy to do. What you want to to run the Live CD.

---

### Post by anon_private on 2010-03-20
Hi,
 
So, following Ozy's advice. either option 1 or 2 should run the 'Live CD' without wiping out, or, effecting Vista in any way. Is this correct?
 
Does 'LiveCD' simply mean running from CD, but not installing?

---

### Post by Ozymandias_117 on 2010-03-21
> **anon_private said:**
> For the one-time boot option. If I use UBUNTU then finish, do I then simply close UBUNTU, remove the CD, then reboot to get back to Vista?
 
For the second option, If I boot from the CD, then I will be using UBUNTU. If I leave the CD out of the drive, I assume that I will boot into Vista. Am I correct?
 
When I read the information on the cover of the UBUNTU CD, I got the impression that I had the option of losing VISTA. Please tell me that there is no chance of removing the Vista operating system from the hard drive when using the UBUNTU CD.



1. Just reboot as though you were in Vista, during the shutdown process it will open your cd tray, ask you to remove your CD and press Enter, then when it turns back on, you'll be in vista again.

2. Exactly

3. As the other poster said, it takes a LOT of steps, with quite a few confirmation boxes to damage Vista, I doubt you would accidentally do anything.

---

### Post by Ozymandias_117 on 2010-03-21
> **anon_private said:**
> Hi,
 
So, following Ozy's advice. either option 1 or 2 should run the 'Live CD' without wiping out, or, effecting Vista in any way. Is this correct?
 
Does 'LiveCD' simply mean running from CD, but not installing?

1. Again, yupperz :)

2. Correct.

---

### Post by craig10x on 2010-03-21
> **anon_private said:**
> Hi,
 
So, following Ozy's advice. either option 1 or 2 should run the 'Live CD' without wiping out, or, effecting Vista in any way. Is this correct?
 
Does 'LiveCD' simply mean running from CD, but not installing?

Yes..that is what it means...in order to install it, you have to click on the "Install Ubuntu" icon and go through a bunch of menus with questions, before it would actually install it...

and that includes your language, time zone, name and password chosen, and how you want to partition your drive (example...wipe out windows entirely....boot side by side with windows...in which case it will divide your hard drive approximately in half between the two systems...

But unless you go into that menu....you are simply running it from the cd itself, and it has NO EFFECT on your Windows Vista...of course, performance won't be as snappy as it would be on the actual hard drive...so keep that in mind...

---

### Post by anon_private on 2010-03-21
Thank you for the very clear replies.
 
I am gaining in confidence.
 
Couple of other points that occur to me.
 
I assume that the CD that they have sent cannot be written to by rogue programmes, or indeed by me. In other words, the CD is in CD-R format. Am I correct?
 
Will my Windows programmes be likely to run under UBUNTU. Will I see them?
 
If a user installs UBUNTU, then later decides to uninistall this operating system, would this be strainghtforward, assuming that they have used  the method of dividing the partition?
 
Best wishes to both
 
A

---

### Post by craig10x on 2010-03-21
even better then running the live cd (where performance will likely be sluggish) why not consider a wubi install....it's not a real hard drive install, it installs ubuntu as a folder in windows and can easily be deleted if you decide to take Ubuntu off your computer...

Wubi will set up a dual boot for you while you have it and if you delete it, then the dual boot is removed from windows)...it's performance will be far superior to running a live cd...almost as fast as an actual install...and will give you a much better idea of how Ubuntu really is..

Only thing about the Wubi install is the largest size you can allocated ot it is 30 gb...other then that it works really excellent...

I did a Wubi install using Ubuntu 8.10 on my Windows Vista...then ended up installing 9.04  with a real hard drive install and decided to wipe out windows altogether..and now run Ubuntu 9.10 and have been windows free for about a year now

Read this article: 
[http://www.linuxbuzz.net/2010/01/easily-install-ubuntu-linux-with-windows-using-the-wubi-installer/](http://www.linuxbuzz.net/2010/01/easily-install-ubuntu-linux-with-windows-using-the-wubi-installer/)

---

### Post by gordintoronto on 2010-03-21
> **anon_private said:**
> Thank you for the very clear replies.
 
I am gaining in confidence.
 
Couple of other points that occur to me.
 
I assume that the CD that they have sent cannot be written to by rogue programmes, or indeed by me. In other words, the CD is in CD-R format. Am I correct?
 
Will my Windows programmes be likely to run under UBUNTU. Will I see them?
 
If a user installs UBUNTU, then later decides to uninistall this operating system, would this be strainghtforward, assuming that they have used  the method of dividing the partition?
 
Best wishes to both
 
A

1. Yes, it's a CD-R, not a CD-RW.

2. Ubuntu has something called "wine" which creates a Windows-like environment for Windows programs.  Some Windows programs work nicely under Wine, some not at all.

Without Wine, or some things which are a lot more complicated, you won't be running any Windows programs. Many, many Windows programs have open-source equivalents. To be honest, they are of varying quality. Many are excellent.

3. Your Windows programs won't be on your desktop. There is a menu called "places," and one of the places is "computer." When you open that (in Nautilus, the equivalent to Windows Explorer), you will be able to see the partitions on your hard drive.  You can double-click to open them and navigate through the folder structure.

You have full access to the files, you can view pictures, open .docs, read PDFs, etc. Because MP3s and DVDs use patented technology, Ubuntu needs additional software, called the "restricted extras," to play them. You can delete files, exactly the same way you would delete them in Windows Explorer.

4. Yes, it's not too difficult to remove Ubuntu.

---

### Post by anon_private on 2010-03-21
I am not quite ready to try this at the moment.
 
Can you address my questions please.
 
Thanks
 
A

---

### Post by anon_private on 2010-03-21
Sorry, I see that my questions were answered - I was on the wrong page.
 
I am wondering why people would want to install UBUNTU under Windows. Obviuosly one can use use either operating system, but why would one want to use two operating systems?
 
I can understand replacing an operating system, but running two?
 
Other than the speed aspect, why not just use the LIVECD for occasionsl accesss where one might need better security than is offered under Windows. This is my reason for considering UBUNTU, and for using on othe machines.
 
Thanks
 
Best wishes.
 
A

---

### Post by craig10x on 2010-03-22
A live cd will have very sluggish performance....at the very least, you should consider a Wubi install...it just makes a separate folder within your windows system...like downloading any program...say yahoo messenger for example...and just as easy to remove if you desire...And the Wubi will perform much closer to an actual hard drive install...

Once you start using Ubuntu....unless there is some programs you can't find the equivalent of in Linux or are a heavy "gamer" you could well decide to rid yourself of windows once and for all... or at the very least have a real install with dual boot and enjoy the benefits of a very secure Os that doesn't have all the "pain in the ----" problems of Windows...such as blue screens of death, viruses, malaware, etc..

Up to you...they have made some good suggestions to you here...your decision if you want to take the advice or not...

I took a chance...and now i am Windows Free....;)

---

### Post by anon_private on 2010-03-22
Thank you for the response.
 
As a matter of interest, how long does it take to load the CD for a Live session? I realise that it will depend on system resources, I am just looking for an approximate figure.
 
If someone installs using Wubi, how much diskspace will be used?
 
Regarding the problems with Windows that you mention, I have never had any of those difficulties.
 
Best wishes.
 
A
 
Ps.  I think one reason why a person might be reluctant to replace Windows is the fact that they bought the pc with Windows installed and, therfore, paid for this operating system. People are often reluctant to divest themselves of something for which they have paid a fee.

---

### Post by craig10x on 2010-03-22
The maximum disk space you can allocate for Wubi is 30gb...you can make it less if you want to...but not more...But once set up...you can't expand it or reduce it, without re-installing it again...

It didn't bother me at all about wiping out windows (even though i paid for it on my laptop) because instead of paying $2700 for a Mac Book Pro 17 i was able to buy a Toshiba Laptop with a 17" screen for $600 at Best Buy and get all the advantage of a Unix based Os without getting locked in to Steve Job's high priced hardware...

Linux gives you much of the advantage of the Mac...but with even more flexibility (because it is Open Source and free)....

Linux, as a unix based Os...doesn't need resource grabbing virus scanners to protect it, doesn't need defragging.....doesn't even have a REGISTRY (which is what usually gets messed up on windows and causes freezes, conflicts and various system problems)..
Just read some articles on the web about the advantages of the system as compared to windows..

Linux doesn't slow down after awhile like Windows does..doesn't need constant "tune ups" and various attention to it to keep it running properly...

Most servers run on Linux for those exact reasons, and that includes most of Microsoft's servers because even Bill gates knows how crappy his Os is....

My friend, who fixes people's windows computers as a side line (he is very computer savvy) since he is retired and it supplies him with an excellent "Cash Cow"...
For his best friends (not customers) he always tells them to install a Linux system like Ubuntu...

To quote my friend "Windows is a real Horror Show" and a dinosaur which gets worse with each new version....take it from someone who knows...
Many people think that most of the computer problems they have are related to their computer...they don't realize that it is the Windows operating system that generates most of the problems they have...

The last year has been the most trouble free and pleasant time i have had with a computer..since i went 100% Ubuntu....Now i just enjoy using my computer and don't have to spend time trouble shooting it...

---

### Post by anon_private on 2010-03-22
Wubi can be allocated 30GB, but can use less.
 
Any idea how much it needs?
 
Thanks

---

### Post by wilee-nilee on 2010-03-23
The basic install takes up 2.5 gigs and I think the ISO stays there so thats 700MB more, I would say give it at least 10 gigs.

I would do a real dual boot rather then wubi though. You will get better performance and not risk losing Ubuntu inside of windows or having problems with updates and upgrades. Wubi was a great idea but falls short in to many areas.

---

### Post by anon_private on 2010-03-23
Thanks for the information.
 
At this stage, I just want to try it out and see what it looks like, how it is used, what's there, etc.
 
So initially, I'll try using the CD in Live mode.
 
If I do this, how long will I have to wait from inserting the CD and booting from the CD drivet o when I can use the operating system.
 
I assume that closing and returning to Windows after booting takes practically no time.
 
 
Thanks again

---

### Post by anon_private on 2010-03-23
Forgot to ask
 
I assume that if UBUNTU is installed under Windows as a type of large file then it will be the subject of the insecurities that are associated with the Windows operating system. Is this assumption correct?
 
If UBUNTU is installed in duel mode form are these same insecurities relevant?
 
Thanks

---

### Post by sixdrift on 2010-03-23
Regarding how long does it take to use Ubuntu after you start boot from live CD...

That really depends on your system and hardware. On some of my older systems it takes a couple minutes. On newer systems, not as long. I think its more hardware dependent from my perspective. Generally on most newer systems its under a minute. But to what extent, that depends on the system.


Regarding how long to get back to Windows after running Ubuntu live CD...

Once you select "Restart" on Ubuntu, it took about 20 seconds to come down and then the BIOS started its boot sequence again to begin the slow march of Windows coming up on a couple of my machines.


Regarding installing Ubuntu under Windows via wubi and vulnerabilities...

Yes, if you are running Windows as a base OS, you are vulnerable. It would be possible for some malware to destroy your Ubuntu installation, but I seriously doubt any Windows malware would be able to get into the internals of the Ubuntu distribution. So it would be safe, but you would still be at risk from simply running Windows.


Regarding installing Ubuntu in a dual-mode setup...

Dual-mode (called dual-boot) is the best bet if you are going to need access to both operating systems in the long run. I keep my machines dual-booted so I can play certain video games on the Windows partitions. That is the only reason I keep Windows. But the dual-boot gives you a clean place to run Ubuntu without worrying about Windows malware interfering (except in the case of some Windows malware destroying the entire disk partition table). So yes, it is safer. But as long as Windows is on the machine, and you boot into it, you will be vulnerable at that time.

---

### Post by anon_private on 2010-03-24
Thank you for the direct and clear answers to my questions.
 
 
Reagrding dual boot.
 
You say that as long as Windows is booted then there is a danger. But in dual boot if one elects to boot into UBUNTU, then presumably Windows is not running?
 
I think you are saying that if Windows is on the disk then there could be problems (running or not).
 
Please feel free to clarify
 
Thanks again
 
A

---

