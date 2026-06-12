---
title: "Segmentation fault errors"
date: 2009-05-03
forum: General Help
---

### Post by dantata on 2009-05-03
I am having some strange segfault errors from time to time. Opera, Transmission and audacious all crashed with such errors within the last several hours. Audacious crashed on several occasions when I was adding songs to the playlist. Opera, on the other hand crashed when I was trying to close a tab. I thought I would ask for some help. 

I ran a memory test (Memtest86) to make sure that the issue is not due to faulty RAM. I also checked the system temperature just in case.

Below is the excert of the log at /var/log/messages:

```
May  3 13:34:45 dn7 kernel: [30720.460656] opera[15405]: segfault at efd3b89e ip 08401529 sp bfcdd210 error 5 in opera[8048000+aa8000]
May  3 14:06:04 dn7 kernel: [32599.180599] transmission[16328]: segfault at fffffffb ip 080b51ad sp b66d2230 error 4 in transmission[8048000+ac000]
May  3 15:05:41 dn7 kernel: [36176.419690] audacious[19152]: segfault at 0 ip 08060230 sp bf9fa460 error 4 in audacious[8048000+cf000]
May  3 17:50:26 dn7 kernel: [ 6743.786948] gsopcast[6664]: segfault at 0 ip b766f0f4 sp bfe45330 error 6 in libc-2.9.so[b75f8000+15c000]
May  3 19:40:28 dn7 kernel: [ 5516.659993] vlc[4838]: segfault at 4 ip b226066f sp b1d55b60 error 4 in libQtGui.so.4.5.0[b20a9000+9c6000]
May  3 19:49:50 dn7 kernel: [ 6078.820049] operapluginwrap[4081]: segfault at 2e746c75 ip 2e746c75 sp bf95f64c error 4

```

Any idea what do the numbers in the [] brackets stand for? For instance, in opera**?[8048000+aa8000]**?

Any help would be appreciated. ;-)

---

### Post by dantata on 2009-05-04
bump!?

---

### Post by BslBryan on 2009-05-04
Hmmm...  Well, it could be that when changing any part of a program, the program creates a file (like adding songs to a playlist is archived for the next run, etc.) and the OS misinterprets that as overwriting part of the OS, causing a segfault?

This is the only thing I can think of off the top of my head...  Want me to Google it for you/with you?

---

### Post by dantata on 2009-05-04
> **BslBryan said:**
> Hmmm...  Well, it could be that when changing any part of a program, the program creates a file (like adding songs to a playlist is archived for the next run, etc.) and the OS misinterprets that as overwriting part of the OS, causing a segfault?

This is the only thing I can think of off the top of my head...  Want me to Google it for you/with you?

I have been googling for other users with the same issue, but no luck yet. Faulty RAM and systemp were both pinpointed as possible causes, but they are not in my case.

I removed Opera, removed ~/.opera and reinstalled it and it seems to be working OK now, just seems. Just when I though the problem was gone Audacious crashed again. I reinstalled it as well. XFCE crahsed a few minutes after Audacious. 

I will wait and see now, I will probably end up trying with a fresh install of Xubuntu. :/

The big problem is that I can't identify the exact problem.

---

### Post by BslBryan on 2009-05-04
This is the first time that I've ever said this, but it looks like a fresh install might be the best option.  

You might want to create a partition to put all of your important files, or just back them up to a disk or drive.  

I'm really sorry I couldn't be of greater help.  I can point you [here]("http://ubuntuforums.org/showthread.php?t=1017754"), but while that might pinpoint why your programs are acting this way, it does not offer any help that I could see.  

Again, I apologise, as this really troubles me.

Best to you, dantata. :)

---

### Post by dantata on 2009-05-04
Yep, I will probably reinstall tomorrow. Will backup any vital info/config files and see if the problem recurs. Will post a follow-up here.

Thanks ;-)

---

### Post by dantata on 2009-05-05
I tried reinstalling twice:

1. with EXT4 partition
2. with EXT3 partition

Both ways - same thing. Too bad - I guess I'll try to live with it; if not I'll probably wait for a new version or another distro to see if the problem persists.

---

### Post by jakes10 on 2010-05-08
I'm using mandriva 2010 on a laptop and have similar problems. Pulse is configured correctly.
So your problem may be wider than you think.

vlc[18952]: segfault at 4 ip b5467343 sp b359bac0 error 4 in libQtGui.so.4.5.3[b52e2000+985000]                                                                                                                   
vlc[22586]: segfault at ffffff94 ip b75dea9d sp b56dd104 error 4 in libpthread-2.10.1.so[b75d7000+15000]                                                                                                          
vlc[24986]: segfault at 4 ip b5be9343 sp b5738ac0 error 4 in libQtGui.so.4.5.3[b5a64000+985000]                                                                                                                   
vlc[18952]: segfault at 4 ip b5467343 sp b359bac0 error 4 in libQtGui.so.4.5.3[b52e2000+985000]                                                                                                            
vlc[22586]: segfault at ffffff94 ip b75dea9d sp b56dd104 error 4 in libpthread-2.10.1.so[b75d7000+15000]                                                                                                   
vlc[24986]: segfault at 4 ip b5be9343 sp b5738ac0 error 4 in libQtGui.so.4.5.3[b5a64000+985000]
vlc[27350]: segfault at 4 ip b5d21343 sp b5870ac0 error 4 in libQtGui.so.4.5.3[b5b9c000+985000]
vlc[29719]: segfault at 4 ip b5c99343 sp b57e8ac0 error 4 in libQtGui.so.4.5.3[b5b14000+985000]
vlc[29719]: segfault at 4 ip b5c99343 sp b57e8ac0 error 4 in libQtGui.so.4.5.3[b5b14000+985000]
X[30277]: segfault at 0 ip 0813445a sp bfde2d9c error 4 in Xorg[8048000+1c4000]
atomix[21571]: segfault at 0 ip b6d8b741 sp bff2f548 error 4 in libc-2.10.1.so[b6d29000+15a000]

---

### Post by morsedl on 2010-06-23
Hi,

I'm also having problems with operapluginwrapper (OPW) segfault'ing (henceforth OPWSF) regularly.

I have both 32-bit and 64-bit Ubuntu on a desktop and laptop.  Both initially installed with karmic (9.10) with Opera 9.x and recently upgraded to lucid (10.04) with Opera 10.10.  No hardware problems, no other segfaults -- or any other errors for that matter -- in dmesg.

Problems with OPW have been there since day one of the first installations (i.e., under karmic).  Flash within Opera works more often than not, but routinely I seem to lose the "connection" between Opera and Flash content.  That is, Flash content is still shown, but all Flash content controls are unresponsive, yet right-clicking on the Flash frame / bounding box does usually still bring up the standard Flash settings dialog.  This suggests to me that the Flash plugin isn't having a problem but the wrapper around it for communicating to-from Opera has died (which typically correlates with one or more OPWSFs).

What I find odd is that I have a Flash Blocker installed, so Flash doens't start on any page for any reason unless I allow it.  Despite this, I still routinely get OPWSFs.  I also seem to get OPWSFs when browsing content that I'm pretty darn sure doesn't have any Flash content at all.

I've not tried backing up and then removing my $HOME/.opera folder since Opera 9.x, so perhaps I'll try that.  I might also try removing plugin's one at a time to see if I can possibly narrow it down to a particular plugin or set of plugins.

Ah, the joys of closed-source software.  Opera should really at least open up the code and provide any necessary libs so folks can test and rebuild OPW as they see fit.  Finally, I see that OPW is a shell script that simply exec's the correct binary.  I wouldn't think it would matter, but I may backup the shell script and copy the correct binary in its place, just to see if perhaps that resolves some strange interaction or timing issue.

Doug


From dmesg:

[ 1168.486449] operapluginwrap[1704]: segfault at 0 ip (null) sp bfe3d62c error 4 in libm-2.11.1.so[110000+24000]
[ 1168.656754] operapluginwrap[1726]: segfault at 0 ip (null) sp bfaaf13c error 4 in libX11.so.6.3.0[110000+119000]
[ 1168.783676] operapluginwrap[1737]: segfault at 0 ip (null) sp bfa24cbc error 4 in libc-2.11.1.so[110000+153000]
[ 1169.305418] operapluginwrap[1772]: segfault at 0 ip (null) sp bfc6e6fc error 4 in libstdc++.so.6.0.13[110000+e9000]

---

