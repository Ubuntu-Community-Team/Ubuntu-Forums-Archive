---
title: "Assorted speed issues with 9.04"
date: 2009-05-07
forum: General Help
---

### Post by Shamem on 2009-05-07
This is rather long, but bear with me. I have tried to provide as much possibly relevant info as possible, but it did end up rather rambling...

[B]
---Backstory---[/B]

Last night i installed Ubuntu 9.04 on my desktop, and have spent hours trying to fix various horrible speed issues. I have trolled through hundreds of threads, both here and on the net in general, and while i have found some fixes(i will outline what i have done), there are still plenty of problems which i can't find a solution for.

I have been running Ubuntu on this machine for years, dual booting with XP, and it worked perfectly, up until now. A couple of months ago(i was running 8.10 perfectly at the time) my hdd partition table threw a fit, and i had to reinstall everything. I was only using my computer for gaming, so i didn't bother installing Ubuntu. Since then i have installed a new graphics card(a ATI HD4870, replacing a X1600XT), but everything else is identical.

Yesterday i needed Ubuntu for uni, so i installed 9.04.

[B]
---Current Issues---[/B]

First problem was that it takes forever to boot. The initial boot is 1min, which isn't to bad for my system(never had the fastest boots, but if anyone has suggestions, it would be great to decrease it), but once Xorg starts to load, this is the sequence of events(or lack of them):

0:00 Black Screen
1:15 Cursor, spinning
1:45 Login screen(auto logs in after 10 seconds)
1:55 Black screen + Cursor
3:30 Desktop Background loads
3:45 Toolbars, missing clock, tray and system monitor
4:30 Clock, etc, show up
4:45 Finish doing everything

That, plus the original 1min boot, gives a boot time of almost 6 minutes, which is VERY annoying.

There is also similar excessive lag on other operations. Opening a lot of apps for the first time for a session, takes forever. For example, Firefox takes 1:30min first time. RhythmBox is similar, as are many other apps.

Further, the first time using sudo causes a 40s hand after entering my password, the first time installing anything with aptitude causes a 5min wait on "(Reading database ...", and opening nautilus on any folder for the first time does the same thing.

During all these delays, the "IOWait" graph on the system monitor applet i have on my top panel shows half to three quarters full. CPU is hardly being used at all.

[B]
---Specs---[/B]

Now for some computer info:
CPU: AMD X2 4200+
GPU: Radeon HD4670
Mobo: Asus A8R-MVP
RAM: 3GB DDR 333MHz
HDD1: 320GB Seagate Barracuda, SATA2, assorted partitions, ~30GB Ext3 for ubtuntu. Note that i originally installed with Ext4, had the speed issues, reinstalled with Ext3, had same issues, and didn't bother reinstalling again before trying other fixes.
HDD2: 500GB Seagate Barracuda, SATA2, NTFS partition(data drive)

[B]
---Other (mostly)Fixed issues---[/B]

When i first installed, i had issues with graphics drivers and general system response, which i will go over in case it is at all relevant.

The whole system was very sluggish(menus, widows, typing, etc), so i tried installing fglrx drivers via jockey, which proceeded to crash, locking me out of installing anything. I restarted, only to get a black screen when Xorg tried to load, indefinitely. I could not switch to any of the tty shells, and was forced to reboot.

I started in recovery mode, and reinstalled fglrx manually, only to have the same problem. After removing fglrx, i finally managed to get an interface with the open source drivers again, with the same sluggishness.
I downloaded fglrx from amd, and installed manually. This seemed to work, but most of the sluggish response and speed issues where still there.
After much forum looking, i added a range of new options to my xorg.conf from other people's solutions, which improved things a bit.

Finally, i found this [bug thread]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186"), and installed the patch. This seemed to fix most of the remaining lag, baring the first run problems outlined above.

One particular problem i had originally was that text input was VERY slow. I was typing a lot faster than the text would show up, to the point that letters went missing. This was particularly evident on tty shells. I'm not sure when this fixed itself exactly, but it seems to be alright now.


**---Finally---**

Ok, i think that generally summarizes my problems. Sorry about the length.
What i am looking for are any ideas as to the boot and app-start issues(though i suspect they are the same).

I won't post any logs or files at the moment, as there are tons that may be related, so if anyone has an idea and needs some more data, ask and i will provide the required file/log.

Any help would be Greatly appreciated. This is all very annoying.

Thanks,

---Shamem

---

### Post by Shamem on 2009-05-08
<bump>

Nobody have any idea what this could be?
It is very frustrating...

---Shamem

---

### Post by Shamem on 2009-05-08
Ok, more information.

My HDDs seem to be going EXTREMELY slow.

This is the output of a hdparm test:

```
sudo hdparm -Tt /dev/sdb

/dev/sdb:
 Timing cached reads:   558 MB in  2.00 seconds = 278.74 MB/sec
 Timing buffered disk reads:    8 MB in  3.20 seconds =   2.50 MB/sec
```

Based on results in other threads, this is ridiculously slow. Am i using hdparm incorrectly? Or is this an issue?

My drives are running in AHCI mode, and are Sata2 Seagate Barracuda drives, as mentioned in OP.

Thanks,

---Shamem

---

### Post by Shamem on 2009-05-09
<Bump>

Does everyone seriously have no clue about this?

---Shamem

---

### Post by Shamem on 2009-05-09
More info.

After having a [look at this thread]("http://ubuntuforums.org/showthread.php?t=678153&highlight=sata+cdrom+slow#9")(the guy seemed to have very similar read speeds to me), i found that lsmod doesn't seem to show any ata modules loaded....

```

lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
snd_hda_intel         434484  3 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
ppdev                  15620  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                61972  0 
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
i2c_ali15x3            14724  0 
parport_pc             40100  1 
joydev                 18368  0 
fglrx                2082308  27 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13316  0 
pcspkr                 10496  0 
snd_timer              29704  2 snd_seq,snd_pcm
i2c_ali1535            14212  0 
shpchp                 40212  0 
parport                42220  3 lp,ppdev,parport_pc
ati_agp                14988  0 
agpgart                42696  2 fglrx,ati_agp
snd                    62628  15 snd_hda_intel,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              15200  1 snd
usbhid                 42336  0 
k8temp                 12416  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
skge                   48272  0 
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Any ideas on this? (Please!)

---Shamem

---

### Post by eyrieowl on 2009-11-11
Wow.  So, I just tried to put Karmic Koala on my machine.  It's a AMD X2 3800, 3 gb ram, 2 500 gb sata drives, radeon 2600xt video...and an A8R-MVP motherboard.  And I am getting EXACTLY the same symptoms as you.  It's unfortunate that you didn't get any responses because I'd sure like to know how to fix my problem without having to replace the computer...it's not going to be easy to simply get a cheap new socket 939 motherboard at this point in time.  In particular, my iowait seems to always be above 40%, even when the system is idle, and hdparm -Tt /dev/sdX (same for a and b) gives me the same numbers as you, ~290 cached, >3 buffered.  If I look at hdparm and dmesg, it sure LOOKS like I'm using UDMA6.  I would have expected DMA to be the issue, perhaps, but that's not it.  I've played with all manner of BIOS settings to see if something was interacting badly...nothing makes any difference, not running AHCI, not running emulated IDE.  I've been doing a lot of Google and I can't make heads or tails of the problem.

---

### Post by Shamem on 2009-11-11
Hey, sorry to hear you have the same issues. Unfortunatly I never found an answer, but if you are getting it does seem to be a mobo issue. I have actually moved on since that computer, and have basically no issues at all with my new one(so far).

If you don't want to buy a completly new computer, try finding a second hand 939 board. I am on the hunt for one for my old machine as the A8R-MVP is now bricked (long story).

Other than that, perhaps the ubuntu community can be more helpful to you than it was to me? :P

---Shamem

---

### Post by eyrieowl on 2009-11-12
well, i did some pricing of 939 boards, they were not as cheap as their vintage would suggest....so i ended up going out last night and buying a sata ii expansion card, turned off the onboard sata entirely, and i am now getting acceptable performance from the computer (~450 cached, ~80 buffered).  I'd imagine it would be even better onboard (and it would get rid of the strange pause i now have in my boot sequence), but i consider it $40 well spent.  This transition from windows to ubuntu has definitely been interesting, to say the least....

---

