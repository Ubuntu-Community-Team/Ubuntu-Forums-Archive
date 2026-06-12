---
title: "Gnome Random Crashes..........."
date: 2005-11-13
forum: Desktop Environments
---

### Post by chrisgibbs on 2005-11-13
Installed Ubuntu 5.10 onto desktop as 2nd boot OS and been having some problems with Gnome just randomly shutting down

When gnome crashes it will just send a logoff command and everything gets killed ( no option of no log off), then just prompts with the normal logon screen like nothing has happened....

Upon reading my messages log time after a crash i discovered this line...

```

**gdm_slave_xioerror_handle :Fatal X Error Restarting :0**

```

(i only included the message without timestamps etc...)

btw the process was gdm that had the problem.

I have googled for a while but i cant find one post or forum post that is similiar to my message.

Anyone have any ideas??

---

### Post by chrisgibbs on 2005-11-13
soz i forgot to say that

Im running 

AMd 64 3000+
Gigabyte GA-K8NSC-939
1gb DDR400 
ATI 9600 PRO 256mb
2 x 80gb SATA HD's

I just completed 4pass's of the memTest and it found no errors....

Also 

5.10 Ubuntu
2.6.12-9-386 kernel
2.12.1 Gnome

---

### Post by chrisgibbs on 2005-11-13
Bump.....

---

### Post by Saiboogu on 2006-01-09
Bumping this again, to see if you (or anyone else) found a solution..

Getting the exact same error in my logs, though I haven't witnessed it firsthand. I have GDM setup to autologin, so I just return after being away from my PC (as little as 5 min once) to find all my apps gone, just a fresh session. Looking through the logs I only have the xioerror message you posted.

Interesting tidbit - that is the exact message that is generated if I manually restart X with Ctrl-Alt-Backspace. I enabled debugging in my GDM config and receive a lot more output with the same timestamp as the xioerror, but nothing that gives me any more clues. No help from Google either... Hopefully someone understands what this is telling me.

```

[COLOR=Red] localhost gdm[7109] Handling message: 'XPID 7127 0'[/COLOR]
localhost gdm[7109] Got XPID == 0
[COLOR=Red] localhost gdm[7109] Handling message: 'SESSPID 7127 0'[/COLOR]
localhost gdm[7109] Got SESSPID == 0
localhost gdm[7127] slave_waitpid: done_waiting
localhost gdm[7127] Session: start_time: 1136766580 end_time: 1136779432
localhost gdm[7127] Sending SESSPID == 0 for slave 7127
localhost gdm[7109] Handling message: 'SESSPID 7127 0'
localhost gdm[7109] Got SESSPID == 0
localhost gdm[7127] gdm_slave_session_stop: saiboogu on :0
localhost gdm[7127] gdm_slave_xioerror_handler: Fatal X error - Restarting :0
localhost gdm[7127] term_quit: Final cleanup
localhost gdm[7127] gdm_slave_quick_exit: Will kill everything from the display
localhost gdm[7127] Running gdm_verify_cleanup and pamh != NULL
localhost gdm[7127] Running pam_close_session
localhost gdm[7127] Running pam_setcred with PAM_DELETE_CRED
localhost gdm[7127] gdm_slave_quick_exit: Killed everything from the display
localhost gdm[7109] mainloop_sig_callback: Got signal 17
localhost gdm[7109] gdm_cleanup_children: child 7127 returned 2
localhost gdm[7109] gdm_child_action: In remanage
localhost gdm[7109] gdm_display_manage: Managing :0
localhost gdm[7109] loop check: last_start 1136766550, last_loop 1136766550, now: 1136779432, retry_count: 1
localhost gdm[7109] Resetting counts for loop of death detection, 90 seconds elapsed since loop started or session lasted more then 30 seconds.
localhost gdm[7109] gdm_display_manage: Forked slave: 12053
localhost gdm[12053] gdm_slave_start: Starting slave process for :0
localhost gdm[12053] gdm_slave_start: Loop Thingie
localhost gdm[12053] gdm_slave_run: Sleeping 1 seconds before server start

``` 

Those lines in red seem to be the start of it all - though I'm not talented enough to actually know what I'm looking at here. Anyway to know what they refer to?

Hardware:
Athlon 64 x2 3800+
ASRock 939Dual-SATA2 Motherboard
2x 1GB DDR400 (dual channel)
NVidia FX-5200
80GB, 200GB IDE drives

Ubuntu 5.10
2.6.15-rc7 with ck1 path
Gnome 2.12.1
GDM 2.8.0.5

Seems like our only similiarity is the Athlon 64. I'm running 32-bit Ubuntu. Didn't try memtest, though you reported yours was clean, so... 

Only other thing that may be worth mentioning, this system was a nightmare to install. Used a Ship-it CD as well as multipled burnt ISOs - all reported failures installing "base system" - finally got it to install by doing a server install, then apt-getting ubuntu-desktop. Then I had to hack in a lot of packages offline (downloaded from XP to a FAT32 partition) to manage a kernel recompile, because the onboard networking wouldn't work. There were several times I thought I had seriously fubared my dependancies, but all seemed well. Perhaps something is still a bit fouled with that, though... 

Its been stable, until I started getting (or noticing..) these crashes. Any clues gang?


[COLOR=Red] EDIT: Probably didn't need to dig this thread up - in case any one else stumbles across it, a simple sudo dpkg-reconfigure gdm seems to have fixed it. No crashes in 24hrs now, enough to prove it to me (when it went down ever 2-3 hours before)[/COLOR]

---

### Post by cdean on 2007-12-17
I'm getting this error, too.

**gdm[6094]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0**

(datetime and hostname omitted)

I, too, have autologin set, but I'm using Gutsy amd64.

I'll try the reconfigure and see how it goes.

---

### Post by xdotx on 2008-01-08
I was having the same problem, tried the gdm reconfigure and it seemed to work for about a day and a half, until it just happened again. Sad times :(

---

### Post by czechman86 on 2008-01-10
i have been having this problem ever since i bought my x86 computer. at first i thought it was an issue with an older kernel, but as i got better with linux, i discovered it was this same error. i hope that the people over at canonical will fix this soon! i love linux and especially ubuntu and dont want to have to switch back because of annoying xserver crashes.

---

### Post by xdotx on 2008-01-27
Just found out I had a bad DIMM slot. Swapped it out and have had no problems since!

---

