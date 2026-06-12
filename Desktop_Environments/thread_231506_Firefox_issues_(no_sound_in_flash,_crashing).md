---
title: "Firefox issues (no sound in flash, crashing)"
date: 2006-08-07
forum: Desktop Environments
---

### Post by fieldstone on 2006-08-07
(I posted this in another one of the forums; I wasn't sure which one was the best to post it in.)

I'm having some serious problems with Firefox (and all Firefox-based browsers) on AMD64 Dapper Drake. Although Flash works in all my browsers, I get no sound. I've tried the symlink method and changing FIREFOX_DSP to "arts", "aoss", and "none", but none of these have any effect. I even have the same problem in i386 Opera, which I installed hoping it would work.

When I run Firefox from a terminal and try to play a flash file, I get the following message:

ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

I'm pretty sure this is my sound problem, but I'm stumped as to how to fix it. Has anyone run into this before?

In addition, sometimes Firefox (or any Firefox-based browser, like Epiphany or Galeon) crashes when I'm typing something into the address bar or search box (or sometimes when clicking a link) - and when it crashes, it completely logs me out of Ubuntu so that I have to enter my username and password again. I find this really bizarre, and I think it's a separate issue.

If anyone can offer me some help on one or both of these issues, I'd be eternally grateful. I've wasted untold hours trying to fix this myself and I can't think of anything else to try.

---

### Post by Dr. Nick on 2006-08-07
did you try setting dsp to "esd" aswell?

Ill link another thread that talks about it, and I will link the thread that helped me solve mine via a different method

[http://ubuntuforums.org/showthread.php?t=223112](http://ubuntuforums.org/showthread.php?t=223112)

This thread fixed sound for me
[http://ubuntuforums.org/showthread.php?t=204022](http://ubuntuforums.org/showthread.php?t=204022)

---

### Post by fieldstone on 2006-08-07
Yeah... with it set to esd, firefox wouldn't load at all. It said the following:

unrecognized option: /usr/lib/firefox/firefox-bin
unrecognized option: -a
unrecognized option: firefox
unable to connect to UNIX socket:/tmp/.esd-1000/socket

I'll try the links you sent me, but I'm pretty sure I've already seen those threads and tried everything in them without success.

---

### Post by PatrickMay16 on 2006-08-07
Yo, man!
Have you installed the package "alsa-oss"? You can't use aoss without it.

---

### Post by someguyouknow on 2006-08-07
i had the same sort of issue and it turned out to be sound related.....
i did this.....
sudo apt-get install alsa-oss

sudo kate /etc/firefox/firefoxrc

FIREFOX_DSP="aoss"

for some, aoss may not work (like for me) so i put auto instead.....
i can watch google video and youtube with no problems now.....
hope this helps someone....

---

### Post by fieldstone on 2006-08-07
> **PatrickMay16 said:**
> Yo, man!
Have you installed the package "alsa-oss"? You can't use aoss without it.

Yep, alsa-oss is definitely installed. Don't know why it won't load, though... I even checked that libaoss.so is in /usr/lib, and it is.

---

### Post by fieldstone on 2006-08-07
> **someguyouknow said:**
> i had the same sort of issue and it turned out to be sound related.....
i did this.....
sudo apt-get install alsa-oss

sudo kate /etc/firefox/firefoxrc

FIREFOX_DSP="aoss"

for some, aoss may not work (like for me) so i put auto instead.....
i can watch google video and youtube with no problems now.....
hope this helps someone....

Yeah, a lot of the guides I saw suggested doing that. The only thing it does for me is make Flash crash more often; it has no effect on sound, sadly.

Is there a different way to enable flash sound in Swiftfox? (I.e., does it have its own separate config file, or does it use the /etc/firefox/firefoxrc file?)

---

### Post by someguyouknow on 2006-08-07
you try setting it to 'auto' instead of 'aoss'
that worked better for me.....
aoss cause more crashes for me as well.....

---

### Post by fieldstone on 2006-08-07
> **someguyouknow said:**
> you try setting it to 'auto' instead of 'aoss'
that worked better for me.....
aoss cause more crashes for me as well.....

That causes a segmentation fault. I wonder why...

---

### Post by bhuot on 2006-10-25
I found a solution. Un-install Flash Player - it solves the problem. Same problem with Flash Player 7 installed via add/remove programs from applications menu and also with Flash Player 9 beta from the Adobe website.

---

