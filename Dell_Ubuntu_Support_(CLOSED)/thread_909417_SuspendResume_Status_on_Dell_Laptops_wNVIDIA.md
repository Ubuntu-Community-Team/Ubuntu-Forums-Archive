---
title: "Suspend/Resume Status on Dell Laptops w/NVIDIA"
date: 2008-09-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aidave on 2008-09-03
I'd like to get everyone's current experiences with suspend resume.  I'm using 1420n with 8.04.1 (installed) and I have to admit the suspend/resume is working far better than with Gutsy.  I am using the NVIDIA driver 173.14.09 driver, which seems to be the cause of increased stability.

That being said, I still have the odd resume crash.  I'd say it is down to 1/15 resumes, it will lock up.  

I also still have the white password screen, about 2/3 of the time, and the regular password screen 1/3 of the time.

Anyone else report their experiences?

---

### Post by dfrandin on 2008-09-03
I have a Vostro 1400 (same as Insp 1420), with Nvidia video, installed Ubuntu 8.04 myself, as the system came with Vista.. Everything on it works 100% under Ubuntu, EXCEPT for standby and hibernate.. Since Ubuntu boots and shuts down so much faster than XP or Vista, I don't really care about getting stdby/hibernate working.. Right after I installed Ubuntu hibernate worked for a bit (about 4-5 times) then all the sudden I started getting a bunch of errors pointing to the uvc driver for the webcam.. I found a fix on the forum for that, but now the system seems to hibernate, but doesnt come back right..  Had to ctl-alt-bksp to
restart X, then the system worked ok... 

Dave

---

### Post by wellybelly on 2008-09-04
I had the same problem with 7.10 on my 1420. 8.04 seems to have (mostly) fixed the issue. Seems to recover ok from hibernate, although still does some weird things on the display. Only upgraded a couple of days ago, so may still have problems as aidave did.

---

### Post by aidave on 2008-09-04
Thanks.  I love Ubuntu I use it at home and work.  I wish this one issue would be fixed somehow.  NVIDIA has a new driver and a new beta driver that may be worth trying.

---

### Post by jkhansen on 2008-09-04
Installed ubuntu 8.04 gutsy on an Inspiron 2100. PIII, 700mhz, 256MB Ram

After the install, on the first full-boot, it seems to boot fine to the log-in screen, but seems to go into suspend mode after just a few seconds.

If I wake back up, I briefly get my login prompt, but not long enough to log in before it suspends again. Been searching high and low, but can't see an answer to this "auto suspend" loop I'm in.

Tried a re-install and then an install of xubuntu 8.04 with the exact same problem. 

Unsure if this is a bios issue or what given that it has happened with the 2 distro's.

---

### Post by jespdj on 2008-09-04
Suspend and resume work normally on my XPS M1530 with nVidia 8600M GT.

I am running 64-bit Ubuntu 8.04.1 with the nVidia driver that comes with Ubuntu (driver version 169.12).

---

### Post by Gausian on 2008-09-07
Suspend is working fine for my M1530.  Occasionally I get an unrecoverable situation where i have to hold in the power button and restart.  But it happens about once every few weeks.  Not sure of the cause, and its definitely bearable.

---

### Post by gjzeus on 2008-09-07
I also have problem with suspend and hibernate for my Dell XPS M1530. I install Vista and Ubuntu 8.04(hardy). 

```

uname -a
Linux **** 2.6.24-19-rt #1 SMP PREEEMPT RT **** x86_64 GNU/Linux

```

The problem is
1. suspend seems ok but scim and port 7634(for hddtemp) were turned off after resuming from suspend. I can start scim manually, but don't know how to turn that port on. 
2. hibernate. Give me this error 
   uvcvideo: Failed to query(135) UVC Control
   it seems webcam cannot be unloaded or loaded normally. 
   And also see message "Hibernate failed" pop up after I successfully come back from hibernation. No idea what's that?

Any help appreciated.

Last dummy question, why do I have to clean my cookies everytime I log in the forum? Even for previewing post?

---

### Post by phenest on 2008-09-07
Have you added the Dell repository? I have a Precision M90, and suspend and hibernate worked better after adding it.

---

### Post by gjzeus on 2008-09-10
These two days i'm too busy. What's the address for dell repositary?
could you post it here?
deb ht..................?


I check the dell linux, and follow the procedure, but got this message
```

wget -q -O - http://linux.dell.com/repo/software/bootstrap.cgi | bash
Unable to determine that you are running an OS I know about.
Handled OSs include Red Hat Enterprise Linux and CentOS,
Fedora Core and Novell SuSE Linux Enterprise Server and OpenSUSE

```

And thank you for your reply.

---

### Post by yoxi5236 on 2008-09-10
forvault.com is newly supplying WOW Gold & [dofus kamas](http://www.dofushq.com)WOW Money, WOW accounts and WOW Quest-help Service .Nowhere you can find the most cheapest price for these sevice.Our company is a [dofus kamas](http://www.dofusmax.com)centric company aiming to bring total satisfaction to your gaming needs.

---

### Post by phenest on 2008-09-10
[http://ppa.launchpad.net/dell-team/ubuntu/](http://ppa.launchpad.net/dell-team/ubuntu/) hardy main

---

### Post by gjzeus on 2008-09-10
Thanks a lot.

---

### Post by aidave on 2008-10-10
Interesting article on suspend/resume in Linux:

[http://lwn.net/Articles/274008/](http://lwn.net/Articles/274008/)

---

