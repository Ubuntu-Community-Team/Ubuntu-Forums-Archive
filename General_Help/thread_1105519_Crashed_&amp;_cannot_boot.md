---
title: "Crashed &amp; cannot boot"
date: 2009-03-24
forum: General Help
---

### Post by Wazzag on 2009-03-24
Hello everyone

I am new to Ubuntu
I installed it four days ago inside XP as dual boot on a slave drive partition (50gig partition, freshly formatted in FAT32)

All updates are installed except one (a kernel of some kind, it was a fault in the download, I don't have the details)
I installed ATI drivers, and after initial glitches with some apps defaulting to m/board sound I got sound/vision effects and everything working sweet
I followed the comprehensive video and sound solutions guides in the multimedia forum and it worked beautifully
I was impressed
Then it crashed, I sent an email and zap, black screen-nothing (email received btw)

After reading another thread I un-installed evolution from the recovery command line but that didn't help (crash occurred just after importing T-bird address book and sending mail)

Re-boots get to the welcome sound then stall with a black screen/text
It has several lines of text, loading ACPI.....starting xxx....doing....x....running.....enabling xxx... the last one being 'checking battery power', all say 'OK'
The cursor is flashing and I can type on the screen

I have to ctlr+alt+del to get out of this

I have run recovery mode but get stuck at the command line after logging in (it has done an auto fsck because of 23 re-boots)
By stuck I mean I don't know what command to bash it with

Comp is about 5 years old, Asus A7V400-MX, 2800+ Sempron, 1gig RAM, ATI X1600pro, Chaintech AV710
Ubuntu 8.10, generic kernel 2.6.27.11

Any ideas?

---

### Post by amadeus266 on 2009-03-24
I'm guessing it has more to do with the video driver. try again and enter "startx"

---

### Post by Wazzag on 2009-03-24
Thanks for the reply

startx gives me a blank screen 

That is no text, nothing

Should I have typed something before (like sudo..etc)

---

### Post by Wazzag on 2009-03-25
Bump

---

### Post by Wazzag on 2009-03-25
I re-installed, thanks for your input amadeus266

---

### Post by amadeus266 on 2009-03-25
If it happens again try ```
sudo dpkg-reconfigure xsever
```
I am willing to bet your xserver settings got skewed.

---

### Post by Wazzag on 2009-03-26
OK thanks

It seems to be running a lot smoother this time
Previous install I had a few 'issues' I had to deal with before the crash
This time everything seems to be working much better

---

### Post by amadeus266 on 2009-03-27
Glad to hear that.

---

