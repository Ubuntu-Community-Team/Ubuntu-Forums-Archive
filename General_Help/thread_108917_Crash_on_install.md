---
title: "Crash on install"
date: 2005-12-27
forum: General Help
---

### Post by Frizl on 2005-12-27
Just bought a brand new clean pc;

Athlon64 3500+
2x512 DDR Ram
250 GB Maxtor HD
ASUS A8N-VM (nForce4) Mobo with integrated audio and video

Tried to install Ubuntu 5.10 32-bit version. The installer hangs at either the partitioning stage or when installing the base system, at random percentages.

I've run a memory test, no errors. I can also run DOS without problems.

What's going on? I'm a newbie at Linux..

---

### Post by adie273 on 2005-12-27
Download the CD image for 64bit systems like yours, you can get it at....


[http://releases.ubuntu.com/5.10/ubuntu-5.10-install-amd64.iso](http://releases.ubuntu.com/5.10/ubuntu-5.10-install-amd64.iso)


Adie

---

### Post by Frizl on 2005-12-27
[QUOTE=adie273]Download the CD image for 64bit systems like yours, you can get it at....


[http://releases.ubuntu.com/5.10/ubuntu-5.10-install-amd64.iso](http://releases.ubuntu.com/5.10/ubuntu-5.10-install-amd64.iso)


Adie[/QUOTE]
Wow, this server is fast! 550 kb/sec!

I thought the 32-bit version would be compatible as well just like regular windows also works on an athlon64...

---

### Post by adie273 on 2005-12-27
Not really sure how 64bit processors work with all 32bit software to be honest. It does provide support for most 32bit software, but I know its not all 32bit software.

If you give that 64bit version of ubuntu a shot, it should work. If not, it'll be some kinda hardware problem.

I suppose around the AMD64's creation, it would have been made with support for 32bit windows in mind, since they were still waiting for the 64bit release of windows, and maybe thats why it runs 32bit windows rather than 32bit linux, what with Windows being the most popular operating system for home users.

---

### Post by Frizl on 2005-12-27
So I tried the amd64 version.. still hangs :(

There's an interesting phenomenon though. During the installation, when partioning, if I create an ext3 partition (along with a swap partition), the process hangs when formatting that partition. If I choose reiserfs instead of ext3, partitioning goes fine, but the installation hangs when installing the base system.

:confused:

---

### Post by adie273 on 2005-12-27
Might be a hardware problem then (NOT in that your hardware is damaged, don't get me wrong.) But maybe something between Ubuntu and your hardware isn't right.

Sorry I can't be much more of a help from here tho.

---

