---
title: "BSG Freespace 2 Mod: How I got it working . . ."
date: 2007-04-15
forum: Gaming &amp; Leisure
---

### Post by Linuturk on 2007-04-15
I had quite a bit of trouble getting Beyond the Red Line working on my Edgy system.

My specs are in my signature.

First, you'll have to grab the torrent of the release. 
[http://www.game-warden.com/bsg/](http://www.game-warden.com/bsg/)

Go to the download section and download the torrent. I'm currently seeding. 

**YOU DO NOT NEED THE FULL VERSION OF FREESPACE 2 FOR THIS TO WORK. IT IS STAND-ALONE.**

After the download finishes, copy the *.run file to a working directory in your home folder. I used a folder called bin in my home folder. This file has to be executable. You can use nautilus or the command line to set it as executable. Before you execute this file, install the **libgtk1.2** package.

Then, execute the file by prefixing "  ./  " in front of the filename in the terminal. A gui installer pops up, and should be fairly easy to follow.

After the install finishes, things got really tricky for me. You can execute the demo using the same method you installed the game with. Simply prefix the btrl_demo file with "  ./  " to run the game.

I ran into a problem because of my intergrated intel chipset. When I attempted to start the first level, I'd crash to desktop, and this output would be in my terminal.

```
$ ./btrl_demo
libGL warning: 3D driver claims to not support visual 0x4b
ERROR: "Could not load ABexp04 anim file" at fireball/fireballs.cpp:697
```

If you run into this, you are lacking something called S3TC with the MESA drivers for your system.

Details are here: [http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html](http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html)

Here is my process for fixing this on my machine.

First, I downloaded this file 

[http://homepage.hispeed.ch/rscheidegger/dri_experimental/libtxc_dxtn060508.tar.gz](http://homepage.hispeed.ch/rscheidegger/dri_experimental/libtxc_dxtn060508.tar.gz)

to a temporary working directory in my Home folder. Next, I made sure I had my **linux-headers and build-essential** installed. Next, I had to install the devel files for the Mesa driver. This was **libgl1-mesa-dev**. This package has dependencies. 

I also installed **driconf** to enable the S3TC module, before installing it. I don't think the order matters, but this is important. This will install a gui config tool that you can use to change this setting, along with other settings.

Next, I went into the working directory via terminal, and ran 

sudo make && sudo make install

That added that support I was missing for my system. Now, I can run the games first level!

Now I have to figure out why my mouse isn't working.

---

### Post by buttons on 2007-04-15
Nifty!  Game worked out of the box here on my nvidia 7800GT.

One silly issue (my fault)...during the first campaign when the instructor lets you operate your craft, my ship started spinning wildly.  I looked through all the keys and became increasingly confused until I realised my PS2 guitar hero guitar was connected, and the game had automagically detected it as a game pad.  For those of you that don't know, PS2 guitars have a strange mapping where the "X axis" is always set to fully left.  Using the guitar's pick to tilt the craft up and down confirmed my suspicions :o

---

### Post by hardskinone on 2007-04-15
Wow, now works but I have serious graphic problem here:

[[IMG]http://img460.imageshack.us/img460/6701/screen0000rw4.th.jpg[/IMG]](http://img460.imageshack.us/my.php?image=screen0000rw4.jpg)
[[IMG]http://img362.imageshack.us/img362/7206/screen0001fl0.th.jpg[/IMG]](http://img362.imageshack.us/my.php?image=screen0001fl0.jpg)

My specs: Dell 640m, Inter Core Due, 945GM

---

### Post by Linuturk on 2007-04-15
Same here. The first level isn't really playable.

[http://www.game-warden.com/forum/showthread.php?t=3919](http://www.game-warden.com/forum/showthread.php?t=3919)

There is my thread.

My guess is our hardware isn't beefy enough.

---

### Post by tehkain on 2007-04-15
What license does this game use? the source included no info.

---

### Post by buttons on 2007-04-16
> **tehkain said:**
> What license does this game use? the source included no info.

Freespace 2 was released under a non-commercial license, according to [the wikipedia entry]("http://en.wikipedia.org/wiki/Descent:_FreeSpace#The_FreeSpace_2_Source_Code_Project").

A little further down it mentions that Interplay reserves the right to withdraw all rights at any time.

BSG is obviously a total conversion of said game, and presumably would fall under the same license (and restrictions), but IANAL.

---

