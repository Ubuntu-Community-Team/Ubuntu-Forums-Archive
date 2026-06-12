---
title: "Xubuntu 19.04 cannot install"
date: 2019-10-13
forum: Desktop Environments
---

### Post by madscintist on 2019-10-13
I cannot install Xubuntu 19.04 on my pc. I'm not sure why this is. Is the ISO corrupted!. I tried writing it to USB multiple times and downloading it multiple times. This is the first for me this has happened been on Linux for long very long time. So i'm thinking the ISO is bad i installed Kubuntu 19.04 and it worked fine. I boot the livecd and the icons and panel are not right they are old ubuntu icons and the panel goes white looks very weird. I also tried switching USB sticks and with the same result.

I 'm running RX 590 AMD card
CPU is 2nd gen 2600k i7
16GB of Ram

---

### Post by Artim on 2019-10-13
There's a msum number to verify before you install it.  Those big ol' long numbers have to match to be sure you have an exact copy of the original iso file.  Also, torrent is better than direct download if you can.

---

### Post by madscintist on 2019-10-13
> **Artim said:**
> There's a msum number to verify before you install it.  Those big ol' long numbers have to match to be sure you have an exact copy of the original iso file.  Also, torrent is better than direct download if you can.

Its saying its OK. Also i downloaded the torrent aswell before thats what i normally use. I have also downloaded the direct ISO few times with same results weirdness? 

```
[FONT=monospace][COLOR=#54FF54]**[mad@scntist**[/COLOR][COLOR=#FFFFFF]** Xubuntu 19.04**[/COLOR][COLOR=#54FF54]**]$**[/COLOR][COLOR=#000000] sha256sum -c SHA256SUMS 2>&1 | grep OK[/COLOR]
xubuntu-19.04-desktop-amd64.iso: [COLOR=#FF5454]**OK**[/COLOR]
[COLOR=#54FF54]**[mad@scntist**[/COLOR][COLOR=#FFFFFF]** Xubuntu 19.04**[/COLOR][COLOR=#54FF54]**]$**[/COLOR][COLOR=#000000] sha1sum -c SHA1SUMS 2>&1 | grep OK           [/COLOR]
xubuntu-19.04-desktop-amd64.iso: [COLOR=#FF5454]**OK**[/COLOR]
[/FONT]
```

---

### Post by madscintist on 2019-10-13
Here is screenshot of the weirdness. Every time i boot up and try to install the installer hangs on the installer when finishing setting up ext4 and root when going to make user spins hangs.

[IMG]https://i.imgur.com/CET3REV.png[/IMG]

---

### Post by guiverc on 2019-10-13
Possible useful : 
[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0) and [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Yes they both apply to Ubuntu, work work equally well for Xubuntu (or any other flavor). Myself I download using `zsync` (downloading differences over prior ISO I provide; like a similar release - saving bandwidth) so I usually skip the first checksum validation - but I never skip the CDIntegrityCheck ("check disc for defects" - where disc refers to cd/dvd/thumb-drive or whatever media you wrote the ISO onto).  If I have a problem installing; I usually re-test the media to verify it wasn't a bad write, or just faulty thumb-drive (a bad bit that will store 1 successfully but not a 0 or other intermittent media flaw). 

(the second wiki page is rather old; I've been tempted to update it, but it'd mostly be cosmetic changes)

---

### Post by madscintist on 2019-10-13
> **guiverc said:**
> Possible useful : 
[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0) and [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Yes they both apply to Ubuntu, work work equally well for Xubuntu (or any other flavor). Myself I download using `zsync` (downloading differences over prior ISO I provide; like a similar release - saving bandwidth) so I usually skip the first checksum validation - but I never skip the CDIntegrityCheck ("check disc for defects" - where disc refers to cd/dvd/thumb-drive or whatever media you wrote the ISO onto).  If I have a problem installing; I usually re-test the media to verify it wasn't a bad write, or just faulty thumb-drive (a bad bit that will store 1 successfully but not a 0 or other intermittent media flaw). 

(the second wiki page is rather old; I've been tempted to update it, but it'd mostly be cosmetic changes)

What did you want me to do? I already checked the ISO as you see

---

### Post by Artim on 2019-10-14
I'm just guessing now, but I found that if I choose *"Download Updates while Installing,"* I get some weirdness as well.  When I *don't* select it, it works fine, and I simply update after the installation is complete and rebooted.

---

### Post by madscintist on 2019-10-14
> **Artim said:**
> I'm just guessing now, but I found that if I choose *"Download Updates while Installing,"* I get some weirdness as well.  When I *don't* select it, it works fine, and I simply update after the installation is complete and rebooted.

Well it doesn't matter if i click it or not. The weirdness and install hang still happens and i have downloaded the ISO about 5 to 6 times now and i have checked the ISO checksum and integrity of the files no error it said but still weirdness. I'm at lost end?

---

### Post by Artim on 2019-10-14
I'm curious - does 18.04 or 19.10 behave the same way?  Perhaps the way to go is install a previous version and upgrade.

---

### Post by madscintist on 2019-10-15
Well, I have to say one thing Xubuntu guys need to re-upload refresh ISO. It's buggy. I managed to install Xubuntu 19.04 this time right now I'm on it. But I would not recommend it to a new user at all. until they get stuff sorted out. I only got one error something about missing something on CD/DVD in the ISO. which is weird. I also didn't use GParted to partition this time or else i think the install hangs. I just used the installer to make my root partition and the 2nd time i did it it went all the way through. 


Now i'm on xubuntu yaaaay 
 :smile: :smile: :smile:

---

