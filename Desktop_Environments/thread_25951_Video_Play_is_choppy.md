---
title: "Video Play is choppy"
date: 2005-04-11
forum: Desktop Environments
---

### Post by pasha on 2005-04-11
Hi.

first of all I love Ubuntu!
I have installed the basic system and enabled
only Ubuntu repositories including universe and multiverse,
with the addition of marillat testing (for libdvcss and libavcodec)

When Totem plays mpeg files the playback is not fluid but choppy.
Xine plays better (less choppy) but is not fluid as expected.

If I play one of the commercial DVD I own, or some DVD I made the playback
in totem is almost impossible (although I have installed the necessary gstreamer-plugins) and even if better in xine I experience a lot of frame drops.
This does not happen on the same hardware when using FC3.

My Hardware : 

PIV 2.6Ghz Hyperthreading
512 MB RAM
Standard Combo DVDPlayer/CD-Burner
Sound Blaster Live!
ATI Radeon 9200 128MB Ram

Prior to open a ticket I would like to know if what I am experiencing is normal or it might be a bug.

- Best Regards
- Pasha

---

### Post by dusu on 2005-04-11
It seems like dma is disabled on your computer.
If your disk drive is /dev/hdc, try :
```
sudo hdparm -d1 /dev/hdc
```
and see if it makes things better

---

### Post by pasha on 2005-04-11
[QUOTE=dusu]It seems like dma is disabled on your computer.
If your disk drive is /dev/hdc, try :
```
sudo hdparm -d1 /dev/hdc
```
and see if it makes things better[/QUOTE]
 Thanks !!!
Now it works like a charm.
My /dev/hdd (the DVD Player) and my /dev/hdc (how could you know it?) were not activated by default.
I have managed to put the commands into /etc/init.d/bootmisc.sh so that it's always enabled.
A little more to go (Transcode & DVDRip + mplayer) and Ubuntu will take over my PC!

- Best Regards
- Pasha

---

### Post by rothbart on 2005-04-11
I've run into something similar.  I can't seem to play video full screen without it being choppy.  When a typical video player goes full screen, is it also using your desktop resolution?  I'm running 1600x1200 desktop and even from DVD it doesn't play smooth.  Xine complains of dropped frames.  I checked my DVD player (not at home right now) and it was reporting DMA was turned on (it's a 4x burner and I burned a DVD in K3b and noticed it's ending speed was 1.58x).  The video problem is not restricted to DVDs.  Playing divx/xvid files is the same.  Mpeg too.  My graphics card is an ATI All-in-Wonder 9800 Pro.  I realize ATI is not ideal for Linux, but it easily handled these tasks under XP (but for all I know it was changing the resolution when I went to full screen).  Any ideas/tips?

BTW, I can play these files (including DVDs) perfectly smoothly at 100% and even at 200%.  My CPU is an AthlonXP 2500+ so while it's no speed demon, it's not too ancient.

--rothbart

---

### Post by pasha on 2005-04-12
Hi.

I am surprised to ear that, because FC1,FC2,FC3 never gave me that problem with my ATI 9200. 
BTW I can play DVD smoothly in Ubuntu, except **Aliens**, in Totem. (Xine succedes).
All other DVDs play fine after enabling *DMA*.
It could be that Aliens DVD is mess up with over copyright protections. 
Now you told me that I will test what happens with divx and mpeg files.  :roll:

---

