---
title: "Please Help S-video Doesn't Work!!!!!!!"
date: 2006-02-20
forum: Desktop Environments
---

### Post by FleetwoodMan1968 on 2006-02-20
I posted on audio/video a long time ago and got no response so I'll post one here to hopefully get this problem resolved. i'm running a 9200 SE ati card but the s-video is in bad shape when ubuntu boots up, the load screen and mem check is all ok. When i tried what was posted on a different thread this is what i got...........

brett@brettmedia:~$ sudo apt-get install linux-restricted-modules-2.6.10-5-386 x org-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.10-5-386 is already the newest version.
The following NEW packages will be installed:
xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 3185kB of archives.
After unpacking 10.2MB of additional disk space will be used.
0% [Connecting to security.ubuntu.com (1.0.0.0)]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted xorg-driver-fglrx 6.8.0 -8.8.25-0ubuntu11.1
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/po...l/linux-restri](http://security.ubuntu.com/ubuntu/po...l/linux-restri) cted-modules-2.6.10/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11.1_i386.deb Could n ot connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis sing?

am i doing something wrong????? Please advise on what else i can do to make this work, i'm starting to get a bit flustered because i cann't use ati's drivers either and i'm running out of options. Thanx for looking

---

### Post by evilgold on 2006-02-21
I'm not sure if it will work, but try adding it as a second display in your xorg.conf. I set my nvidia card up that way...but nvidia is a bit more linux compatable from what i understand.

try this post, but only the part about xorg conf, and translate all nvidia stuff to whatever ati driver your using currently. [http://www.ubuntuforums.org/showthread.php?t=96765](http://www.ubuntuforums.org/showthread.php?t=96765)

Just for kicks, i might try to get my lappy (Radeon M7500) to work with s-video tomorrow, in which case i'll let you know of my results, but for now thats all the help i can provide.

---

### Post by FleetwoodMan1968 on 2006-02-21
Alright, thank you, i'll re-post and let you know what happens

---

### Post by FleetwoodMan1968 on 2006-02-21
ok, that was a little vauge, i'm kinda' new to linux, the most programming i ever did was VB but that was more then 10 years ago that I messed with that so most of that is gone out of my head by now, if there is something a little more step by step that's out there that would be helpful, or if someone could walk me through it, also keep in mind i've been trying to get this to work for 3 days now so I'm also a little flustered seeing as how it took one dang code just to get online and i messed with that for almost 5 days i think, so basically what i'm saying is is there an easier way, i have 3 more computers to set up on this network, and this one should be the main pain in the butt one, 'cause after this i have to figure out how to set-up my hauppage card on here with myth-tv.  Thank's for the help.

---

