---
title: "Games in vmware slow, linux-rt kernel needed?"
date: 2007-11-25
forum: Gaming &amp; Leisure
---

### Post by MaximusTG on 2007-11-25
I've been using ubuntu for some time now, and though I don't play a lot of games anymore, I do like playing the occasional Red Alert 2 skirmish. Sadly this game runs reeeeeally slow in Wine. So I figured, why not run it in VMWare. My system specs:

Intel Pentium Dual Core E2180 (2x2.0 GHz)
2 GB PC5300 DDR2
Asrock motherboard with Intel GMA950 Graphics
320 GB 8MB cache SATA HDD
etc.

Should be more than enough to run Red Alert 2 in VMWare(with windows xp sp2 installed on the virtual machine). However, it still runs a bit choppy and slow..
I'v read some stuff about a real time kernel (sudo apt-get install linux-rt). But I can't find anything about this combination. 
Does anyone have experience with running games in VMWare? Couldn't hurt to try the real-time kernel I suppose..

---

### Post by hikaricore on 2007-11-25
Games aren't meant to be run under virtual machines.
There is no direct video hardware access yet in most virtual machines..

No kernel in the world will change this.

---

### Post by KhaaL on 2007-11-25
Try installing the vmware host drivers (not sure what they're called) to boost performance.

---

### Post by mikedep333 on 2007-11-25
I am surprised that RA2 runs slow under wine. However it looks like there is a solution right here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=252](http://appdb.winehq.org/objectManager.php?sClass=version&iId=252)

You may need to update wine

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by MaximusTG on 2007-11-26
Well, I already have the latest Wine, and that solution, using opengl rendering didn't work for me. However, I found out that the game runs super if I switch to 16 bpp. That caused other problems, with video output, and my theme looks really bad in 16 bpp. So I have looked up how to make a second x-server, with 16bpp. I made a script that launches the second server, and then starts the game. Works fine.
But I don't know how to automatically kill the x-server when I quit the game.

---

### Post by jpew on 2007-12-08
It is a common misconception that a real time kernel is "faster" than the normal kernel, however this is not the case.

The point of a a real time kernel is to provide mathematical guarantees about the operation of the threads it is running, such as "thread X" will have finished executing by time "Y". A common example is a sensor application where there is some sensor attached to the computer that *must* by polled at a specified rate, then pass the data to some other userland application for processing. RT Linux can guarantee that the sensors will be polled at the specified rate, then you can run some program to process it in userspace. Also, RT Linux doesn't run processes (programs), only kernel threads.

At any rate, long story short, the average person will have no need for RT linux, and it probably wouldn't make their system faster even if they could run their normal applications in it.

---

