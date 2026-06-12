---
title: "Steam freezes desktop on launch"
date: 2014-02-03
forum: Gaming &amp; Leisure
---

### Post by BoogeyOfTheMan on 2014-02-03
Whenever I try to start Steam, it just freezes my whole desktop, causing me to have to hard reset my PC. I'm not certain what could be causing this, I'm leaning towards a graphics driver issue, but I can play the Minecraft and other graphics accelerated apps just fine.

I had had Steam installed and running perfectly for a while, but at some point my graphics card stopped working, so I went back to onboard graphics. And again, everything was working fine. Then I got my Nvidia card working again, and now Steam freezes on launch.

My bootstraplog has an entry for what looks like every file in the .steam directory that looks like:

[2014-02-03 14:05:10] BVerifyInstalledFiles: ubuntu12_32/vgui2_s.so is -1 bytes, expected 918729

I've tried removing it and reinstalling it twice. Anybody got any ideas?

OS=Kubuntu 13.10
KERNEL=3.11.0-15-generic
CPU=Intel Haswell i5-4570S @ 2.9ghz
MEM=16gb DDR3
GPU=Onboard Intel / Nvidia GTX 580
DRIVER=Nvidia 304.116

---

### Post by dannyboy79 on 2014-02-04
can you try to use a newer nvidia driver than what you're using? and or what does the terminal spit out if you launch steam from a terminal?

---

### Post by BoogeyOfTheMan on 2014-02-04
I've tried using the newest driver from the Nvidia site (331 I think) and 319 from the x-swat ppa and I couldnt get either to work. I've removed and reinstalled jockey, removed everything Nvidia before trying the newer drivers. 

When I try from the terminal, it spits out a lot of ```
BVerifyInstalledFiles: ubuntu12_32/vgui2_s.so is -1 bytes, expected 918729
```, over 2,000 lines. And then it freezes X. The other night I got it to instead of freezing, it just crashed X and brought me to the session login, by trying ```
STEAMRUNTIME=0 steam
``` in terminal. And then it actually put some info in my xorg.log ```
[ 50633.227] (EE) Backtrace:
[ 50633.228] (EE) 0: /usr/bin/X (xorg_backtrace+0x3d) [0x7ff8b6b7bfdd]
[ 50633.228] (EE) 1: /usr/bin/X (0x7ff8b69d9000+0x1a6d49) [0x7ff8b6b7fd49]
[ 50633.228] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7ff8b5ad9000+0xfbb0) [0x7ff8b5ae8bb0]
[ 50633.228] (EE) 3: /lib/x86_64-linux-gnu/libc.so.6 (0x7ff8b46f3000+0x8120d) [0x7ff8b477420d]
[ 50633.228] (EE) 4: /lib/x86_64-linux-gnu/libc.so.6 (__libc_calloc+0xbf) [0x7ff8b477706f]
[ 50633.228] (EE) 5: /usr/bin/X (0x7ff8b69d9000+0x7cf6d) [0x7ff8b6a55f6d]
[ 50633.228] (EE) 6: /usr/bin/X (CloseDownClient+0x57) [0x7ff8b6a2d727]
[ 50633.228] (EE) 7: /usr/bin/X (0x7ff8b69d9000+0x55296) [0x7ff8b6a2e296]
[ 50633.228] (EE) 8: /usr/bin/X (0x7ff8b69d9000+0x447ba) [0x7ff8b6a1d7ba]
[ 50633.228] (EE) 9: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7ff8b4714de5]
[ 50633.228] (EE) 10: /usr/bin/X (0x7ff8b69d9000+0x44aff) [0x7ff8b6a1daff]
[ 50633.228] (EE) 
[ 50633.228] (EE) Segmentation fault at address 0x0
[ 50633.228] (EE) 
Fatal server error:
[ 50633.228] (EE) Caught signal 11 (Segmentation fault). Server aborting
```

I'm thinking about trying the newer drivers again today and if that doesnt work, maybe a fresh install. I really dont want to have to do that though.

---

### Post by Perfect Storm on 2014-02-05
Isn't that a hybrid videocard? If so you need to use the bumblebee driver instead.

---

### Post by BoogeyOfTheMan on 2014-02-05
As far as I'm aware, it is not a hybrid card. Its a big beastly thing that barely fits in my case. And I've had it working perfectly before, but some update in Dec decided to make it give me headaches.

---

### Post by BoogeyOfTheMan on 2014-02-07
So I ended up doing a fresh install. There's something about a clean install that excites me for some reason.

Well, on the install, the nouveau drivers worked great. For a couple of hours at least. Then when I was trying to install Dropbox, the screen went black and started displaying messages from nouveau. After a reboot, it happened again (also while trying to install Dropbox), this time it let me hit Ctrl-Alt-F4, but the input was really slow and it kept displaying the nouveau messages in between whatever I was trying to type. It let me Ctrl-Alt-Del, and when it booted up this time, it just froze everything (again, trying to install Dropbox, I keep an encrypted copy of my password file in there, so I needed it so I could login here). So I went back to my onboard graphics :(

I'm guessing either the power supply or the graphics card is bad. (My cousins PC "died" and she decided to give me the whole thing to part out, and those were the only 2 parts I used). Now I'm all sad. That graphics card was ~$500 new and still goes for ~$260. And the power supply that I got when I built this box is only 430w, and the card needs a minimum of 600w. I guess I'll buy a new power supply when I can afford it and retest.

Thank you everyone for your help.

---

