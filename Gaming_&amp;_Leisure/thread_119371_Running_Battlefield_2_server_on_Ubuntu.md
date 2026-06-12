---
title: "Running Battlefield 2 server on Ubuntu?"
date: 2006-01-19
forum: Gaming &amp; Leisure
---

### Post by dreadthenight on 2006-01-19
I'm looking for advice on running a Battlefield 2 server on Ubuntu.  Has anyone done this?  How is the performance compared to running BF 2 on MS Win2k/XP?  I'm relatively new to Ubuntu and it's the best distro I've found, now I'm wondering if I can use it to run a Battlefield 2 server.

Thanks!

(Also posted to Ubuntu Server Talk)

---

### Post by Azion on 2006-01-19
There is a linux server already made by EA.
It's on their website, this is a dedicated server.
I've heard the performance difference is null.
I haven't noticed any difference when on a Linux or Windows server.

---

### Post by dreadthenight on 2006-01-19
Hi Azion,

I was browsing Google Groups this morning for posts that had to do with BF 2 and Ubuntu.  I see some people having problems getting the EA files installed properly but no solutions yet.

---

### Post by Azion on 2006-01-19
Have you already tried the linux server install?

---

### Post by dreadthenight on 2006-01-19
Nope, not yet.  I don't have a machine that I can dedicate for it, but am looking for one now.  Just trying to find out whether I can do this with Ubuntu or whether I should stick with XP.

---

### Post by Azion on 2006-01-19
Do it with ubuntu.
I've heard of no problems with the linux server.
As well it'll give you a chance to dabble with Linux

---

### Post by jackmacokc on 2006-02-19
I run BF2 1.2 dedicated with no problems in ubuntu. Let me know if you need help setting it up. Just PM me.

---

### Post by bjweeks on 2006-02-20
I got it setup also. To use bf2cc you must install mono tho.

---

### Post by DexterBelgium on 2006-02-20
Same here, BF2 1.2 server through bf2cc, just installed the server packages, installed mono from synaptic, got bf2cc, been happy ever since. Gonna try running a public server at the lan I'm visitin this weekend (1200+ gaming Belgians, gotta love it). 

Was just about to reply to this thread when I saw the replys. I have only been using ubuntu on a server box for a month, and installing bf2server plus Bf2 CC was one of the easier things to do (other than installing stuff straight from synaptic, that is, man, that is a joy, but i digress)

Just try it, it is easy, and will put a smile on your face :-)

---

### Post by Tullyamo on 2006-03-10
i have installed the 1.1.2 server on my ubuntu machine and have special forces and normal bf2 install on my windows machine.  when i sh start.sh the ubuntu server it goes through all the pregame and starts the server.  my windows machine has never been able to see the ubuntu machine in the server list on lan.  is it a version mismatch?  the ubuntu machine is set to lan, ip XXX.XXX.XXX.21 and never shows up in the update server list.

---

### Post by WildTangent on 2006-03-12
I've got it installed as well. I had to do quite a bit of symlinking and bash scripting to reduce the complicated procedure for running it to a simple "sudo bf2ded" in the terminal...

-Wild

---

### Post by jellisii on 2006-04-22
Sorry to zombie this thread, but I have a question directly related to this:  I have Breezy installed on an older P4 (non-M) laptop, and while everything else I've installed to the machine works great, the BattleField 2 server cores after about 20 to 30 mins of run time, pretty consistantly.  The dump messages have don't resemble anything that I've been able to dredge up online (alas, the almightly Data Overlord Google has failed me!), so I figured I'd turn to the people who have used this distro more than I have for advice!

The one thing that I *have* noticed is that I can't run a remote X session (I use Cygwin to talk to the machine from my game rig, because I can) and the BF server simultaneously, as it bombs them both, so I SSH into the box as the dedicated bf2 user to run the start command.  This isn't a problem, but something I bring to the table as information that may pertain to my problem.  I have no problems running a remote X session otherwise.  

I have not tried to daemon-ize the process (I haven't looked to see if it was possible yet, but the server doesn't need privs, so I haven't tried it yet either), but I really don't want it to run all of the time either.    

While typing this, I wondered if it may be that the SSH session is timing out on me, but this happens when I use screen as well, so I don't believe that to be the issue.  I will turn up sshd's ClientAliveInterval and ClientAliveMax settings to check this potential issue.

Here's the nuts/bolts of the setup.  Pardon me while I abuse the code tag:
```
~$ uname -a
Linux osiris 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686 GNU/Linux

~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/Ubuntu-root
                       9137892   2629712   6508180  29% /
tmpfs                   257988         0    257988   0% /dev/shm
tmpfs                   257988     12588    245400   5% /lib/modules/2.6.12-10-3
86/volatile
/dev/hda1               248948     47860    201088  20% /boot

~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge
(rev 05)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (r
ev 05)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Co
ntroller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (r
ev b2)
0000:02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev
 78)
0000:02:04.0 CardBus bridge: O2 Micro, Inc. OZ6912 Cardbus Controller

~$ cat /etc/apt/sources.list (comments removed)
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

Pentuim 4, 1.4MHz
512 MB RAM

```
A quick parse of the core files with gdb points to a segfault but most of the informative stuff that I'd be able to use to figure out the problem with comes up as "??", as opposed to actual information.  I don't code in C, so I'm not really in a position to do more than poke around with what tools I can read about.  I can post the core files if someone wants to look at them.  

This may be something hardware related, but I think I would see it other places if this was the case.

---

### Post by jellisii on 2006-05-05
Bump for great justice!  Just once to see if anyone who might look here may have any ideas.

---

