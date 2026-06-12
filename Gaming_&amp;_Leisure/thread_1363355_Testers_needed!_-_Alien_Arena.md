---
title: "Testers needed! - Alien Arena"
date: 2009-12-24
forum: Gaming &amp; Leisure
---

### Post by Irritant on 2009-12-24
For Alien Arena -

Since our last release's compiled binaries caused so many problems for Ubuntu users, what we would like to do is pre-emptively strike with some test binaries first.  

Who can test?  You **must be using the SVN version of Alien Arena and be up to date, and be using a 32 bit system**.  Copy these files into your alien arena directory, and try to run them.

[http://www.sendspace.com/file/rtq49q](http://www.sendspace.com/file/rtq49q)

Thanks, and let me know if they work ok!

---

### Post by Irritant on 2009-12-24
Holy hell, bump.  

Trying to prevent all the issues with the last couple of releases here people :)

---

### Post by Cope57 on 2009-12-25
I would rather have a 64 bit version, a full packaged .deb would be nice.

---

### Post by Irritant on 2009-12-25
> **Cope57 said:**
> I would rather have a 64 bit version, a full packaged .deb would be nice.

Sure, but that's not what we are testing right now.  Most people have 32 bit systems, so that is what the binaries are going to be compiled to by default.

But, if you want to compile the 64 bit version and get it to Strat, that'd be awesome :)

---

### Post by ahood on 2009-12-25
I am occasional gamer and like to assist from time to time. I have played Alien Arena and enjoyed it. I would like to test, but I have some questions first.

Is there a link on how to compile and install the test build or is there instructions included in the downloaded archive?

What is the minimum specs?
I have a low-end machine (1.8 GHz, 2 Gb RAM, GeForce 7800 GT)

Where does one report any error messages or other feedback?

Is testing recommended for Ubuntu user that doesn't mind enter commands in a terminal but definitely not an expert?

What version of Ubuntu is recommended for testing?

Regards,

---

### Post by darkstaar on 2009-12-25
I could go for this as I have a bit of time on my hands but I'm running 64-bit.

Bump, anyway. And Merry Christmas.

---

### Post by Melcar on 2009-12-25
You know, you can simply do a symbolic link with the 32bit libraries to get it working on 64bit.  Saves the hassle of re-building the game.
Anyway, the provided binaries work for me.  System is a laptop running Ubuntu Karmic 32bit (2GHz Sempron, 2GB RAM, 200M IGP).  I still have to do the sound workaround (create .alsoftrc) for the game to work tough, but I guess that's a whole different problem.

---

### Post by Irritant on 2009-12-25
Thanks Melcar, that's what we were hoping to hear :D

---

### Post by Perfect Storm on 2009-12-26
I'm going to sticky this for a week, as so many people are playing Alien Arena and have trouble with it.

---

### Post by MaxIBoy on 2009-12-26
Here's an SVN guide for Alien Arena. I wrote the Linux section:
[http://alienarena.wikia.com/wiki/SVN](http://alienarena.wikia.com/wiki/SVN)
Just scroll down to where it says "Linux Guide," and follow the directions to checkout Alien Arena from SVN and compile it. If you can compile it, that means you have all the dependencies installed OK. That should help narrow down some false positive bug reports. The main reason (I assume) this is being done, is because the stock binaries for 7.32 were compiled against libjpeg7 instead of libjpeg6 The workaround was to have people recompile it. If it works when it's compiled but not with the stock binaries, that means there's some kind of issue with the stock binaries again. I'm pretty sure that's what the devs are fishing for.

---

### Post by Melcar on 2009-12-26
But for the purposes of this testing you shouldn't compile it.  Just pull the svn branch, download the files from the OP, and copy them into the Alien Arena folder (game.so goes inside the *Game* subfolder).  You may still need to perform the sound workaround for the game to run.

---

### Post by MaxIBoy on 2009-12-26
> **Melcar said:**
> But for the purposes of this testing you shouldn't compile it.  Just pull the svn branch, download the files from the OP, and copy them into the Alien Arena folder (game.so goes inside the *Game* subfolder).  You may still need to perform the sound workaround for the game to run.
Thanks for pointing that out, I clarified my post.

---

### Post by Syndri on 2009-12-30
wait why are you guys having problems it works fine for me
download it from here

[http://www.playdeb.net/updates/category/FPS](http://www.playdeb.net/updates/category/FPS)

---

### Post by DasEi on 2009-12-30
nice hint to the deb, I ask for the version, the deb is 7.3.21  , the svn is 7.3

---

