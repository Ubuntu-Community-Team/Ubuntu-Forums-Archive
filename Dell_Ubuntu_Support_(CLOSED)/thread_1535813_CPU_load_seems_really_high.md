---
title: "CPU load seems really high"
date: 2010-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DManX04 on 2010-07-21
I've been having some problems with my system consistently lagging lately, and I was wondering if anyone could give me any advice.

Here are my symptoms:
1) CPU usage after a reboot is consistently between 20-30%, even when no other programs are running. It gets as high as 70-80% if I've got a few programs running (typically OpenOffice, Firefox, File Browser, and Skype or a PDF viewer).
2) Approximately every 10-30 seconds I get some type of screen freeze up that lasts a second or two. For example, I'll be moving my mouse, and it will stop for a moment before jumping across the screen, or I'll be typing something and the letters will stop appearing on the screen briefly and then suddenly the entire sentence will show up. This happens most frequently when I'm scrolling up or down in windows, whether I'm using the scroll bar on the window or on my touchpad.
3) I've run top, and, even with Firefox running two windows with a few tabs each, only 5 or 6 programs are using the CPU, with none listed at more than 7%. Most are typically shown below 4%. Earlier I did have one Firefox window with like 10 or 12 tabs open, and npviewer.bin was using 80-100% CPU.

This all started a few weeks ago, and it has been getting worse. I can't think of anything I've added, but I did remove a bunch of the alternative flash players one day (gnash, swfdeck, etc.) and re-installed just Adobe Flash. That was several weeks ago, though, and the problem has only gotten out of hand in the last week or so.

---

### Post by bobcollard on 2010-07-23
> **DManX04 said:**
> I've been having some problems with my system consistently lagging lately, and I was wondering if anyone could give me any advice.

Here are my symptoms:
1) CPU usage after a reboot is consistently between 20-30%, even when no other programs are running. It gets as high as 70-80% if I've got a few programs running (typically OpenOffice, Firefox, File Browser, and Skype or a PDF viewer).
2) Approximately every 10-30 seconds I get some type of screen freeze up that lasts a second or two. For example, I'll be moving my mouse, and it will stop for a moment before jumping across the screen, or I'll be typing something and the letters will stop appearing on the screen briefly and then suddenly the entire sentence will show up. This happens most frequently when I'm scrolling up or down in windows, whether I'm using the scroll bar on the window or on my touchpad.
3) I've run top, and, even with Firefox running two windows with a few tabs each, only 5 or 6 programs are using the CPU, with none listed at more than 7%. Most are typically shown below 4%. Earlier I did have one Firefox window with like 10 or 12 tabs open, and npviewer.bin was using 80-100% CPU.

This all started a few weeks ago, and it has been getting worse. I can't think of anything I've added, but I did remove a bunch of the alternative flash players one day (gnash, swfdeck, etc.) and re-installed just Adobe Flash. That was several weeks ago, though, and the problem has only gotten out of hand in the last week or so.
To see where most of your CPU is used run the following command in Terminal:
```
top
```

---

### Post by tkoco on 2010-07-24
> **DManX04 said:**
> I've been having some problems with my system consistently lagging lately, and I was wondering if anyone could give me any advice.

Here are my symptoms:
1) CPU usage after a reboot is consistently between 20-30%, even when no other programs are running. It gets as high as 70-80% if I've got a few programs running (typically OpenOffice, Firefox, File Browser, and Skype or a PDF viewer).
2) Approximately every 10-30 seconds I get some type of screen freeze up that lasts a second or two. For example, I'll be moving my mouse, and it will stop for a moment before jumping across the screen, or I'll be typing something and the letters will stop appearing on the screen briefly and then suddenly the entire sentence will show up. This happens most frequently when I'm scrolling up or down in windows, whether I'm using the scroll bar on the window or on my touchpad.
3) I've run top, and, even with Firefox running two windows with a few tabs each, only 5 or 6 programs are using the CPU, with none listed at more than 7%. Most are typically shown below 4%. Earlier I did have one Firefox window with like 10 or 12 tabs open, and npviewer.bin was using 80-100% CPU.

This all started a few weeks ago, and it has been getting worse. I can't think of anything I've added, but I did remove a bunch of the alternative flash players one day (gnash, swfdeck, etc.) and re-installed just Adobe Flash. That was several weeks ago, though, and the problem has only gotten out of hand in the last week or so.

Sounds like a laptop with limited memory (like my laptop:D ) If you do not use Bluetooth on the system, Use Synaptic Package Manager and totally remove all "BLUEZ" packages. The Bluetooth stack can consume a lot of resources. If you do not have a CD/DVD burner on your system, remove all burner software. If you do not use the Tracker search tool, remove it.

The point I am making here is that certain software is loaded by default whether you use it or not. The daemon support for the software can steal CPU time running up the CPU % usage. By removing the unused/unwanted software, you can free up CPU time and make your system more responsive. Does that make sense?

---

### Post by vangop on 2010-07-26
I'm wondering why people quote full posts anyway...
To the point - use top command to find out the cause (or you're saying that top is not detecting it? So what is reporting high CPU then). When I have cpu spikes this is mostly due to :
1. firefox flash player (plugin-container)
2. Xorg, in most cases related to 1.
3. Skype espec. during the calls. 
4. pulseaudio - related totally to 3.

I was fighting with cpu usage by skype/pulse but didn't find any solution. My thread is still out there with my question only..

---

### Post by bobcollard on 2010-07-26
> **vangop said:**
> I'm wondering why people quote full posts anyway...
..
Because we are lazy and like to see what we are answering right in front of us.:D

---

### Post by DManX04 on 2010-07-28
I just ran top while I was having experiencing very slow patch, and firefox-bin, npviewer.bin, and x-org are the leading culprits. None are consistently high, but all of them are fluctuating between 20% and 80% CPU usage. 

And I don't think it's a memory thing. I've got 2GB RAM, 19.2GB hard disk space, and a 2.2Ghz Intel Duo Core processor.

Are there any temp files of hard disk maintenance I could do that might help?

---

### Post by nexx on 2010-07-28
I have a similar problem : cpu at 100%

top says that root is running at 89% cpu, what is that ?

 5003 root      20   0  8052 1564 1304 R 89.0  0.3  55:09.84 backend

info backend says that it have something to do with cups (printing), and the wifi printer is disconected.

---

### Post by bobcollard on 2010-07-28
See my screen-shot for comparison: a different Distro listed below.

---

### Post by nexx on 2010-07-28
Here is my console, backend is taking over 91% cpu

all that beginned with the sound not working: made it work with the command

gksudo users-admin

then clicked on a box to select me ae a sound user, reboot and it worked, but the cpu is still at 100%

---

### Post by nexx on 2010-07-28
resolved using htop in administrator console and killing the 2 root process that where going amok.

---

