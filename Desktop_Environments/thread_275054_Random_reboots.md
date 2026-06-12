---
title: "Random reboots"
date: 2006-10-10
forum: Desktop Environments
---

### Post by jonread1983 on 2006-10-10
My system keeps randomly rebooting. Not every hour, but every other day. Its not hardware related as i swap the drive with Windows every now and again, and it runs happily until i tell it to shut down.:confused::confused::confused:

For example today i turned my pc on at 6PM. I went the pub at 8.30, PC quite happy. Got in at 11.30 to find it sat on the logon screen, not as if I'd locked it, but as if the system had rebooted and was waiting to log on. This must happen twice a week at least.

Its happened a few times where i was once in Firefox, once in XMMS, and one just about to fire up the terminal. When it happens is doesnt halt itself, it just cuts off, no warning, and reboots.

This is a small extract from the syslog. I've determined the reboot time to be about 10.58pm.

> Oct 10 22:17:01 localhost /USR/SBIN/CRON[11472]: (root) CMD (   run-parts --report /etc/cron.hourly)
Oct 10 22:32:08 localhost -- MARK --
Oct 10 22:52:08 localhost -- MARK --
Oct 10 22:58:49 localhost syslogd 1.4.1#17ubuntu7: restart.
Oct 10 22:58:49 localhost kernel: Inspecting /boot/System.map-2.6.15-27-386
Oct 10 22:58:49 localhost kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Oct 10 22:58:49 localhost kernel: Symbols match kernel version 2.6.15.
Oct 10 22:58:49 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Oct 10 22:58:49 localhost kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
Oct 10 22:58:49 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
What other logs will be of use to determine the cause? :confused:

I wouldnt normally be bothered but the system runs folding at home. If it reboots itself, it stops folding. Once it had gone for about 5 hours of wasted folding time before i realised it had rebooted and then I had to start the FAH session off again. So this is a problem for me.

---

### Post by apjone on 2006-10-11
have you got sufficent cooling? its not infront of a radiator or sat on a BBQ? It sounds like a Thermal reboot.

---

### Post by jonread1983 on 2006-10-11
I think the cooling is sufficient..... The case side has a mesh to allow air in, the rear of the case has a 120mm NMB server fan, and an akasa PCI exhaust. Theres plently of air flow, and i whipped the case side off to feel the CPU heatsink and it seems normal.

---

### Post by apjone on 2006-10-11
hmmm........ strange...... have you got anything crond? have a look in /var/log/messages aswell

---

### Post by s_p_a_r_k_y on 2006-10-11
i had a weird error with powernowd which froze my laptop whenever I am not connected to power and it changes frequencies. Try turning off services you don't need. Also it could be a memory issue with a bad stick.

---

### Post by vallini on 2006-11-09
Hi !

Have you, by any chance, managed to solve the problem ?
I'm experiencing the same weird behavior but with some differences; I have a desktop PC (it sounds like you have a laptop) and the reboot occurs randomly sometime at night (not while I'm at the pub ;-) ).

What happens is:
I leave the computer (with Edgy) running Azureus all night ('cause of big downloads ;) ) and in the morning I find it like it just restarted, with the logon screen showing.

I examined all the system's log files but I cannot find any strange entry.

I also checked the at/cron for any possible mistake but there is nothing there either.

Could this possibly be a BUG ?

Please someone out there help !
I'm on the verge of re-installing the lot  !
Thing is, I installed it from scratch on a clean partition no longer than a week/10 days ago and didn't mess around with it very much ;-)

Cheers
VAG

---

### Post by tscharf on 2006-12-04
I am also having this *exact* problem since I upgraded to edgy.  I am seriously considering downgrading back to dapper, as I never experienced this problem there. 

I am using a desktop system that has run reliably for years, doesnt have any cooling or memory issues I am aware of.  Furthermore, the system will also reboot itself if I just leave it at the desktop with nothing running!  I have looked through all the logs, and can not find a thing to indicate whats rebooting the machine.

Is this a known bug in edgy?

tscharf

---

### Post by ~zoey~ on 2006-12-07
I have also been having random reboots.  I have been running Dapper and it just started the reboots this past week.  It was fine before.  I don't think that it is an overheating problem.
   :confused: zoey:confused:

---

### Post by miggl on 2006-12-07
I'm having the same issues! I'm glad to see that I'm not along in this ;-). Mine will reboot both when I'm away, or working on something, or playing games, so it's random (I haven't been able to see a pattern so far). If it reboots when I'm at the computer I immediately check the temps and they are all at or below 55C, so it shouldn't be a heat-related reboot (I set that to 75C).

---

### Post by drwesty on 2006-12-19
I too am having random reboot problems with Edgy.
Interestingly I have just found that it seems to do a random reboot very quickly (under 2 minutes) when I have connected to the box via VNC from my laptop (over a modem not over the lan. Working from my other PC on the lan seems fine).

Running IBM eServer with S3 Savage 4 video and Adaptec scsi.

---

### Post by raygeeknyc on 2007-01-07
Same here, I have a machine running in a colo facility. It was stable until about 4 days ago and has rebooted daily.  The first two times was close to cron.daily time so I thought it was that but last night it happened at 11:45 PM.  There's no warning in /var/log/messages and I'm running smartd which reported an error on one day but nothing since.  I could test RAM but since the machine is remote and serving, that's not easily done.

I'm hoping that someone will get some leads posted on this thread,  Anyone out there have an idea as to a good way to diagnose this?

---

### Post by jasonpero on 2007-01-15
So it looks like i *won't* be finding the answer to thiis one on the forums today.
Same problem with an IBM eserver.  fresh install + updates.  Well, 2 IBM eservers.  The first one kept restarting, so I figured it might be a machine specific issue (like ram) so I tried installing on the next one down in the rack, that was a no-go as well.  It seemed to happen the most often though when I was trying to copy some files over and went to minimize a window or move a window.  It didn't like multitasking much at all.  Screen would lock for about 3 seconds and then it went black and restarted.  Must have done the install about 6X today with a slow USB 1.1 cd-rom drive. ](*,)

---

### Post by jasonpero on 2007-01-16
here's some additional info that may help--when the eserver restarts, it pops this error up rather quickly
unexpected NMI at 0000:0000

---

### Post by jasonpero on 2007-01-17
removed dapper drake from the eserver and installed edgy--no more problems.

---

### Post by addux on 2007-11-21
Allow me to be the 20th person to reiterate this problem.  I've only experienced it once (about 20 min. ago) my log is very similar to this log, ie. nothing really to reveal what happened.  As far as thermal restart, my thermal gauge was read slightly above 60 C.  I was running Azureus, and Beryl I just installed a new version of ipw3945, all things I've done before (namel Azureus and Beryl) and I usually leave my comp on for days without any problem.  

Thus ends my bug-free run of using Ubuntu of about 2 months or more.....woohoo

---

### Post by Robstarusa on 2008-06-25
I have this same problem on a freshly installed hardy on Tyan 1U on socket 939.  Cpu temps are in the 40's.  It happens every 2-5 hours.  No problems with gutsy.

Anyone?  This is driving me crazy!

---

### Post by miggl on 2008-06-25
Ever since I moved away from the 939 socket CPU (I completely rebuild my system with new MoBo, CPU, GPU) the problem went away. I have a strong suspision that the 939 CPU was deffective, as it ended up getting worse, and eventually I was unable to reboot into windows (it immediately rebooted after post, and eventually didn't even start anymore).

---

### Post by jorge.maravi on 2008-06-26
Hi guys
My case is kind of weird, I just installed a ubuntu server 7.10 with proftpd, SSH server and samba server. I shutdown today the server using init 0 as root the server was down and after a couple hours the server was up and runnning!!!! Do you guys had a problem like this?

---

