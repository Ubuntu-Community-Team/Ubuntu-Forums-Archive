---
title: "Trouble Running Second Life"
date: 2007-10-08
forum: Gaming &amp; Leisure
---

### Post by MasterNetra on 2007-10-08
Hi I was wondering if anyone knew how to take care of this problem, i downloaded the Linux Client and placed in a directory and according to them all i have to do is go into terminal (or similar) and set my location to the client's directory and type ./secondlife   . Well I did that and this is what happened.

bin/do-not-directly-run-secondlife-bin: error while loading shared libraries: libELFIO.so: cannot open shared object file: No such file or directory
Unclean shutdown.

*********************************************************
This is an ALPHA release of the Second Life linux client.
Thank you for testing!
You can visit the Linux Client Alpha Testers forum at:
[http://forums.secondlife.com/forumdisplay.php?forumid=263](http://forums.secondlife.com/forumdisplay.php?forumid=263)
Please see README-linux.txt before reporting problems.


Any ideas as to how i can get it working? btw i am currently using Ubuntu Feisty Fawn, waiting on the solid release of GG.

---

### Post by eye208 on 2007-10-09
It seems something went wrong during download or extracting the archive. The missing library should be included.

I downloaded numerous versions of the client, extracted them (right-click, "extract here") and then ran the "secondlife" script from the folder either by double-clicking it or from a terminal window. It always worked that way.

---

### Post by MasterNetra on 2007-10-09
I have done that, nothing happened with i tried to run secondlife from double-clicking it. It just says its a executable file but when i choose run from its options, nothing happens. I try to run it from the terminal it does the same thing as before which is failing to load because it can't find those files. In fact I had extracted it and tried running it from the start.

---

### Post by MasterNetra on 2007-10-09
...

---

### Post by eye208 on 2007-10-10
If you can't find the library in the extracted folders, your download was probably broken or incomplete.

---

### Post by MasterNetra on 2007-10-10
bah its alright i guess i had to reinstall windows...Linux doesn't seem to want to reconize some of my hardware regardless of distro. Such as my CD-RW Oh well i guess i could aways save them for when i have the cash flow to build a linux specific computer :/. Meanwhile I'll try the Windows Version of Second Life. Thanks anyway :)

---

### Post by denali on 2007-10-11
> **MasterNetra said:**
> bah its alright i guess i had to reinstall windows...Linux doesn't seem to want to reconize some of my hardware regardless of distro. Such as my CD-RW Oh well i guess i could aways save them for when i have the cash flow to build a linux specific computer :/. Meanwhile I'll try the Windows Version of Second Life. Thanks anyway :)

First and foremost, Second Life on Linux is in Alpha.  It works pretty well, but it can be a bit nutty at times.  If you're not comfortable in running pre-release software and you are desperate to use Second Life, you may want to continue through with your plan to use the Windows version.

Next, make sure you downloaded 1.18.3.5.  That is the latest version as of this message.

Third, your system must meet the following requirements:

[PHP]Minimum requirements:
* Internet Connection: Cable or DSL
* Computer Processor: 800MHz Pentium III or Athlon, or better
* Computer Memory: 256MB or better (strongly recommend more!)
* Linux Operating System: A reasonably modern 32-bit Linux environment
is required. If you are running a 64-bit Linux distribution then
you will need its 32-bit compatibility environment installed.
* Video/Graphics Card:
o nVidia GeForce 2, GeForce 4mx, or better
o OR ATI Radeon 8500, 9250, or better
(nVidia cards are strongly recommended for the Linux client)

**NOTE**: Second Life absolutely requires you to have recent, correctly-
configured OpenGL 3D drivers for your hardware - the graphics drivers
that came with your operating system may not be good enough! 

For a more comfortable experience, the RECOMMENDED hardware for the Second
Life Linux client is very similar to that for Windows, as detailed at:
<https://secondlife.com/corporate/sysreqs.php>[/PHP]

From personal experience, if you have an nVidia video card that uses the old "Legacy" drivers, forget it.  It won't work.

If you've got the above down cold, you're next step would be to open the Synaptic Package Manager and do a search for the missing library there. If you find it, tell Synaptic to install it.  Once all the necessary libraries are on your hard drive, it should run like a champ if you have everything else in place.

---

### Post by eye208 on 2007-10-12
> **denali said:**
> If you've got the above down cold, you're next step would be to open the Synaptic Package Manager and do a search for the missing library there. If you find it, tell Synaptic to install it.
No.

SL comes with all the libraries it needs. Nothing has to be installed via Synaptic for SL to work. The viewer will run out of the box on a default Ubuntu install with either ATI or Nvidia accelerated video drivers. The installation procedure should not take more than 2 minutes.

I wonder why it is so hard for the OP to check the contents of the SL folder. The missing library should be in the "lib" subfolder. If it's not there, it's because the archive was broken or its directory structure was not preserved while unpacking it. Stop doing fancy things on the command line unless you know what you are doing. Right-clicking the archive and selecting "unpack here" will work just fine. I've done it numerous times with every SL update during the past 9 months.

---

### Post by MasterNetra on 2007-10-12
I'll just save Ubuntu for when i eventually build myself a new PC. Naturally making sure the parts can efficiently be used by Ubuntu :)

---

### Post by hp59dk on 2008-09-24
Hi, i have trouble too
It used to work all right till i got the 64 bit system, and i hope it will again.

I posted this here:

[http://ubuntuforums.org/showthread.php?t=302203&highlight=second+life&page=2](http://ubuntuforums.org/showthread.php?t=302203&highlight=second+life&page=2)

but this tread seems to be the right place to post.

I was reading the Second Life txt file because i can not run it. It says that a Linux Operating System should have A reasonably modern 32-bit Linux environment. If you are running a 64-bit Linux distribution then you will need its 32-bit compatibility environment installed.

I am running a 64-bit distribution. Can You tell me what this means? How can i know what to install?

Thank You from Hans Pedersen

---

### Post by Ximal on 2008-09-30
well when in doubt and having trouble... If u have a really good system.. I usually keep a backed up old copy of windows millenium from my gateway installed as a virtual machine so I can run all my windows programs with a specified amount of ram etc.. Then u can just install ur normally ran windows games on ur virtual pc aka vmachine windows x ... as i call it... and play without the unix enviornment crashes and fixes to deal with ....u can also alter ur asm files to help it become more complient... since i prefer to play with the old millenium and 98 gold editions ... they were my favorite....

anyhow.. msg me any time for help with this game... I'll gladly do what i can to help u .. As I run 32 nd 64 bit systems... 

Now as to u running 64 bit systems... Please specify your distrobution of ubuntu. As I run the 7.x on my desktop and my 8,x on my laptop due to it's greater compatibility to an 64 bit system !

---

### Post by MasterNetra on 2008-10-01
Atm I'm duel booting Ubuntu Hardy and Windows XP. Need XP to run CS3 and 3Ds Max for my college classes. At any rate apparently there is no real support for my particular Intel Graphics card in the windows version...Would that translate to the linux version as well??

---

