---
title: "Gnome freezes immediately after login"
date: 2006-12-13
forum: Desktop Environments
---

### Post by Nameless_one on 2006-12-13
I have a strange problem with my Ubuntu Dapper. I am on a dual boot machine, and today, after I ran Windows, doing common things I have done many times in the past, when I rebooted into ubuntu, I encountered this:

The login screen appeared normally, but after I logged in, in the middle of gnome's startup, everything froze (except for the welcome sound which finished normally. Even the mouse stopped responding. No desktop was shown, just a blank bar on the bottom. 

I tried booting up an older kernel, but the results were the same. I also tried a liveCD, and, as weird as it may sound, the exact same thing happened, except there was no login (as it was a liveCD). However, booting up in recovery mode, and starting gnome manually with 

```
/etc/init.d/gdm start
```

everything went just fine, I logged in and gnome ran beautifully, except for an error: "Failed to initialize HAL!". I found this is related to the USB devices, so I suppose it is unrelated, probably a side effect of the recovery mode. By the way, HAL also started just fine from bash. Or maybe it isn't unrelated :) I don't know. 

So, help? Please?

---

### Post by rlozano on 2006-12-13
this seems to be a common problem is some machine model. what's your pc specs/model?

---

### Post by Nameless_one on 2006-12-13
AMD Athlon 2000+ box, ATI Radeon 9200, 512 mbs of RAM. Been on dual boot for a couple of months now, how come it happened now?

---

### Post by Nameless_one on 2006-12-13
Anyone? rlozano said this is common. What did other users do? Should I upgrade to Edgy? 

I forgot to mention I have very low disk space in the partition containing the / folder (m /home folder is in a seperate partition). Could this be the culprit? If I solve this will everything be OK?

---

### Post by Nameless_one on 2006-12-14
Bump.

---

### Post by RudolfMDLT on 2006-12-14
Low disk space as in 100's of megs or 100's of kilobytes? by removing some files you should be fine. I had a not so similar but related problem.

Cheers,

Rudolf

---

### Post by joselin on 2006-12-14
I had the same problem, and i solved it changing my kernel packages from 686 to 386.

Regards.

---

### Post by Nameless_one on 2006-12-14
Well, what do you know. It was the space. I gave my root partition double space and everything loaded beautifully. Like a charm.

---

### Post by RudolfMDLT on 2006-12-15
:)  cool!

---

### Post by domino1241 on 2007-02-26
I am currently having this EXACT same problem.  I was playing around with Aireplay and Airodump trying to learn about securing my wireless network, and now when I reboot I get as far as the login screen, but about 5 seconds after the login screen starts (regardless of what I do; sign in, try the menu, etc) the computer freezes.  However, I noticed that if I don't touch anything the computer makes the noise of signing in and starting up, which makes sense because I had it on a 5 second timed login.  After about a bazillion tries I realized the computer was freezing up IMMEDIATELY when the light on my wireless adapter came on.  I took it out (PCMCIA) and presto, no more problem.  However, when I plug it in after the operating system starts, it freezes again as soon as the adapter lights up.  What's going on here?  Did Aircrack/Aireplay/Airodump somehow ruin my configuration?  If so, how do I fix it?  I'm going to try completely uninstalling everything I put on there but other than that, what can you do to fix this?  And the harddrive space isn't my problem, I have over 15G free.

Thanks!

---

### Post by skaspels on 2008-06-16
I was having the same problem Nameless_one was having - I've been using Ubuntu for a few weeks now, everything was working fine, but just recently when I try to log in, just after logging in, the computer freezes at the light brown screen.

I tried booting manually, (```
/etc/init.d/gdm start
```) from recovery mode, but it still froze after log in.  I checked my space (i used the command df) from the recovery mode line and the readout was thus:
```

FileSystem      1K-Blocks     Used    Available    Use% MountedON
/dev/hda1       28107164      2134892 24544500     9%   /
varrun          127928        12      (and so on)       /var/run
varlock         (similar to above)
procbususb      (ditto)
udev            (ditto)
devshm          (ditto)
lrm             127928        17580   110348       14%  /lib/modules/2.6.17-10-generic/volatile

```

Nothing has helped me, I don't see any space issues here, but if there are, I think I might need to be walked through them.  I was engaged in updating my system before this crash started, and I noticed that my computer no longer recognized my files (it couldn't open my file shortcuts becuase it said that it didn't have a method of handling them, or something like that) on the system, and I wondered why, so I tried restarting, which is when the computer started freezing up.

N.B. I'm Using a Compaq Evo, loaded exclusively with Ubuntu.  I wiped Windows off of the computer before loading Ubuntu on).  I'm afraid I may have to reload the operating system.  Can anyone help?

---

