---
title: "Any update manager freezes on VNC"
date: 2008-11-28
forum: Desktop Environments
---

### Post by concorde106 on 2008-11-28
Hello all,
    I have a really old (i believe it is 1999) Pentium III 450, and am planning to run it as a headless server. Anyways, it currently is running a full Xfce desktop. I have it set up so I can VNC into it from my PowerBook G4. (in case your wondering, it is a mac laptop from 2005.) When I start Synaptic or Update Manager, it gets to "building database file" or something about building a database, and it just stops. I mean, I can use other applications, but the package manager freezes. It is not yet headless, and when I physically use the computer, it's fine. I think that it is that the VNC uses up some internet speed, but when I have accessed it using VNC, I can surf the net with only a small speed hit. What can I do to solve this? Should it be moved to the server forum? I am pretty good with k/x/ubuntu, especially compared to my family. My dad is pretty good with computers, although mostly Windoze machines. (I am trying to  keep pretty Micro$oft free). The stuff in the server forum looked pretty out of my league. Thanks for any help you can provide! (Hey, the spell check says Micro$oft is spelled right! Woo! Anti-Micro$oft!).:lolflag:

---

### Post by sjmahler on 2008-11-28
Maybe I can provide some additional information on my setup.

I have a XUBUNTU 8.10 with VNC4.  Goal to run it headless.  I access XUBUNTU from an XP system running VNCVIEWER4.  It took a couple of hours to get VNC up and running but most things seem to work.

But, if I run APPLICATIONS>SYSTEM>SYNAPTIC PACKAGE MANAGER
or
              APPLICATIONS>SYSTEM>LANGUAGE SUPPORT

the database builder starts and the progress bar seems to stop about 50% of the way thru the process.  I only seem to be able to stop it by running TOP, getting the PID, and sudo kill -TERM.

If I use the hardwired console, both packages operate without problem.

Any suggestions?

...S

---

### Post by concorde106 on 2008-11-28
Ya know, sjmahler? I think it may be the internet connection. Because the VNC connection has to go through my router, and that is... I think.. Well, the wireless internet is 11 mbps, so I think that that would slow down the connection alot. I wonder if their is anyway to overcome that...:confused:
[See this also...(click here)]("http://ubuntuforums.org/showthread.php?t=996087")

---

### Post by gurlinux on 2008-12-15
> **sjmahler said:**
> 

But, if I run APPLICATIONS>SYSTEM>SYNAPTIC PACKAGE MANAGER
or
              APPLICATIONS>SYSTEM>LANGUAGE SUPPORT


Hey! EXACT same problem here. I was looking for some 'precedent' and it looks I found it. Running Xubuntu 8.04.1, intended to become a headless server.

Looking a little further, I found that Synaptic hangs while trying to download "translation_en-CA" packages info or something like that. I tried changing the 'locale' to 'en-US' but it did not help.

Then of course, trying to load APPLICATIONS>SYSTEM>LANGUAGE SUPPORT hangs while loading.

Did you find a solution?
Thanks

---

### Post by gurlinux on 2008-12-23
OK, for the record, I found the SOLUTION!

There is a known [bug]("https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/224447") (or probably a few) on version 4.1.1, which is the latest one available on the repositories.

But [this guy created the 4.1.2 deb packages for Hardy]("http://www.francescosantini.com/index.php?page=linux&lang=en") which I downloaded directly from his website and after installing them everything worked just fine!

Grazzie Francesco!!!

---

