---
title: "Can't start X after Dapper upgrade"
date: 2006-07-22
forum: Desktop Environments
---

### Post by michaelb on 2006-07-22
I upgraded to Dapper, and now I can't start X Windows.
---
I started upgrading to Dapper, following the directions found at [http://ubuntuguide.org/wiki/Dapper#Upgrading_Ubuntu](http://ubuntuguide.org/wiki/Dapper#Upgrading_Ubuntu) . I finished 'sudo apt-get dist upgrade', and then I had to leave the house and I didn't have a chance to reboot. Then I had a power failure, and my computer shut down. I'm not sure if the hard-reboot caused by the power failure changed anything, or if it was just upgrading to Dapper that did it. Now, when I boot up, I just get:

```
Cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
```
Then I'm dumped to a terminal.

I looked around, and found a post ( [http://www.ubuntuforums.org/archive/index.php/t-37103.html](http://www.ubuntuforums.org/archive/index.php/t-37103.html) ) that suggested trying:
```
sudo dpkg-reconfigure xserver-xorg
```
I went through all of the config menus, and nothing has changed. It seemed to recognize my card correctly.

This is quite irritating--my computer is mostly useless right now.

For a desktop environment, I use Gnome. For hardware, I have a NVidea GForce 4 graphics card. My computer is surge-protected.

I should make it clear that everything was working flawlessly before this (on Breezy).

Any suggestions?

---

### Post by llamakc on 2006-07-22
Were  you using the "nv" driver or the NVidia drivers for X?

---

### Post by taurus on 2006-07-22
Do you happen to use nvidia for your video card?  If yes, then you probably need to install a driver for it.  Otherwise, look in /var/log/Xorg.0.conf (or something similar to that) to see what's the problem is...

---

### Post by ardchoille on 2006-07-22
I've never had a dist-upgrade from one Ubuntu version to another go correctly, it always broke the entire system and it was easier and quicker to re-install from the CD of the new version. I followed documentation exactly, step by step, but it doesn't always work for every system.

I'd stick to installing from cd or ISO.

---

### Post by michaelb on 2006-07-23
> **ardchoille said:**
> I've never had a dist-upgrade from one Ubuntu version to another go correctly, it always broke the entire system and it was easier and quicker to re-install from the CD of the new version. I followed documentation exactly, step by step, but it doesn't always work for every system.

I'd stick to installing from cd or ISO.

Ok. Now what should I do? Can I just try upgrading from a Dapper CD, over the botched dist-upgrade installation? Or will that mess things up more? I assume upgrading from CD wont disturb my home directory.

Also, if I should update from CD, should I use the usual Dapper CD, or the alternate image install? 

I'm sorry if this is found somewhere in the documentation and I didn't see it.

---

### Post by michaelb on 2006-07-24
Please pardon my bump, but I really would like to know what to do now.

Thanks.

---

### Post by llamakc on 2006-07-24
Show us the output of `lspci` and the contents of your /etc/X11/xorg.conf for starters.

---

