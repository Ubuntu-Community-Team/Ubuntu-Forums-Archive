---
title: "GDM fails to start (intermittently) after wake from hibernation"
date: 2006-07-17
forum: Desktop Environments
---

### Post by austen on 2006-07-17
I'm having an odd problem. The fun part of the problem is that it doesn't occur 100% of the time, and I don't know precicely what is going on so I'm having a hard time searching for possible solutions. I'll disclose my detective trail thusfar after the specifics.

I'm running Dapper 6.06, current on all updates, kernel 2.6.15.26 on my Dell Inspiron 1100, P4 2.4GHz, 768MB ram, i810 video chipset. I am a recent convert to Ubunto coming from Debian Sid.

WHAT HAPPENS:
-------------

I'll hibernate my system. Everything goes okay. When I power up to wake from hibernation my system will boot, and load the image to resume. When X starts up it begins cycling through some mysterious process. It appears that it will initialize the display, give me the spinny-disk, then crashes, then tries to re-init the screen, and so on...

Durring this (endless) cycle I'll get GDM style error popup-boxes. I've seen two different errors. One is a "HAL failed to initialize", and the other dissappears too fast for me to read, and I haven't seen anything in my logs to indicate what it could possibly be.. :)

WHAT I'VE DONE THUSFAR:
-----------------------

I've googled for the HAL probelm thinking that might be what is causing my problem. I haven't ruled it out, but I'm beginning to think that it isn't HALd. All of the threads I've read about HAL causing booting delays involve smbfs mounts in /etc/fstab, which I have none as I only mount network drives when I need them, and only for as long as I need them.

My syslog reports, inbetween 8 billion lines of (unrelated) networkManager logs I've sifted through:

--------------
gdm[4527]: Error reinitilizing server
gdm[3090]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
gdm[3106]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
--------------

and

--------------
gconfd (austen-5303): Received signal 15, shutting down cleanly
gconfd (austen-5303): Exiting
gconfd (austen-5290): starting (version 2.14.0), pid 5290 user 'austen'
--------------

My GDM log reports:

--------------
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux loki 2.6.15-26-686 #1 SMP PREEMPT Fri Jul 7 19:48:22 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 16 22:41:13 2006
(==) Using config file: "/etc/X11/xorg.conf"
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
error opening security policy file /etc/X11/xserver/SecurityPolicy
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
Error in I830WaitLpRing(), now is 2063646932, start is 2063644931
pgetbl_ctl: 0x27fe0001 pgetbl_err: 0x49
ipeir: 0 iphdr: 7f003b6f
LP ring tail: 50 head: 0 len: 1f001 start 0
eir: 0 esr: 10 emr: ff7b
instdone: c1 instpm: 0
memmode: 0 instps: 53
hwstam: fffe ier: 82 imr: 53c iir: 0
space: 130984 wanted 131064

Fatal server error:
lockup

Error in I830WaitLpRing(), now is 2063648946, start is 2063646945
pgetbl_ctl: 0x27fe0001 pgetbl_err: 0x49
ipeir: 0 iphdr: 7f003b6f
LP ring tail: 58 head: 0 len: 1f001 start 0
eir: 0 esr: 10 emr: ff7b
instdone: c1 instpm: 0
memmode: 0 instps: 53
hwstam: ffff ier: 0 imr: ffff iir: 0
space: 130976 wanted 131064

FatalError re-entered, aborting
lockup
-------------

My work-around for this problem has been to hard-boot the system, which gives me several days of uninterrupted, problem free computer use. I can sleep and wake up many times before this error pops up again.

Anyone have any ideas on what may be going on? Any help pointing me in the right direction would be appreciated!

Thanks!

---

### Post by Mezmerize on 2006-07-19
I also have this same problem, but it got worse... gnome-panel crash then everything that i try to run would segfault immediately.
even terminal won't open.
I'm surviving on a live cd.
Help please!:-k

---

### Post by ovistanciu on 2006-07-27
Same problem here, on a Dell Inspiron 5150. When I wake my laptop from hibernation it starts the Ubuntu boot check (the orange thing) and I get "ok" for the first 2 items (don't remember what they were), and then 2 screen  filckers like austen described before, and then a blank screen. No error messages.

---

### Post by austen on 2006-07-30
Welp... A friend of mine pointed out that X appears to be crashing because it is trying to start by poking more data into video memory than there is video memory available...

Anyone know a way I can set X to force a lean startup when waking from sleep mode? Holy Munchkins Batman... I'm not even sure where to begin with this...

---

### Post by sulobanks on 2006-08-02
I haven't tried to hibernate my desktop, but I was having a similar problem where gdm would completely freeze (except in my case, I got nothing but a blank screen).  I installed kdm and switched to it.  Problem was solved. No more freezes.  Who knows? Might make a difference in this case too?

---

### Post by dasyar613 on 2006-08-02
This is really interesting, my system goes into a hibernate at least 5 times a day, and the only problem that I have is that HAL message that pops up. Other than that, everything is working as it should. So far completely satisfied with Ubuntu.

---

### Post by chrisgibbs on 2006-08-17
The original post is the exact same problem im having.

I get the GDM cycle of trying to start, but i never manage to get to the point of seeing error messages. 

I will see the spinning 'loadin' icon and then the screen will turn off and then back on again.

I'm running a LG LS50a laptop and previously (Hoary) had no problems at all using hibernation.

Anyone got any ideas on where the problem might be?

---

