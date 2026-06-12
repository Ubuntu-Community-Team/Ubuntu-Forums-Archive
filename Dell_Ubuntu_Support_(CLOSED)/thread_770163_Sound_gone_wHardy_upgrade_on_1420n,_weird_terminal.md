---
title: "Sound gone w/Hardy upgrade on 1420n, weird terminal issue"
date: 2008-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jswhite on 2008-04-27
Just finished up the upgrade to hardy, which is friggin' awesome. I've got the Inspiron 1420n, started with feisty, upgraded now all the way to hardy. I'm digging the desktop effects, which I couldn't get under gutsy because of the whole blacklisting thing with the video card.

Anyway, like many others, after the upgrade I was left with no sound. I found the directions on the [Dell Ubuntu Wiki page]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade"), but I've run into a problem implementing them. When I open a terminal and type in the commands, it spits this back at me:

"sudo: unable to resolve host dell"

I can get off anything not requiring a sudo, but anything that does require it gives me that error. I managed to uninstall the modem driver & backports package via Synaptic (which I can launch through the menu, but not through the terminal), but the last steps about rebuilding initrd I'm stuck on because I don't know how to do them without the terminal (if it's even possible).

Hopefully, there's an easy fix for the sudo error. Any suggestions?

---

### Post by WanderingStar on 2008-04-27
Sounds like there is a problem with your hostname configuration.  I'm not sure what your hostname should be (you picked it ;)) but you could boot into recovery mode and edit /etc/hostname and /etc/hosts to ensure the proper hostname is in there and matches. 

For more info: [http://www.ducea.com/2006/08/07/how-to-change-the-hostname-of-a-linux-system/](http://www.ducea.com/2006/08/07/how-to-change-the-hostname-of-a-linux-system/)

---

### Post by jswhite on 2008-04-27
It should properly be "dell", as that's the only thing that it's ever been. And, to be clear, I didn't pick that, Ubuntu came pre-installed on this system, so it was already selected for me. However, before the upgrade, I've never had a problem with it working correctly.

Contents of /etc/hostname:

dell

Contents of /etc/hosts:

127.0.0.1 localhost
127.0.1.1 dell.linuxdev.us.dell.com dell.Homegroup

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by WanderingStar on 2008-04-27
Not positive here, but it looks like the entry for your system in /etc/hosts is mucked up - I believe it should match exactly /etc/hostname. For instance, my /etc/hostname (my system is named osaka):
```
osaka
```

and my /etc/hosts:

```
127.0.0.1       localhost
127.0.1.1       osaka

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I would try to change the second line in /etc/hosts to be just "dell" instead of what it is now.  Perhaps something got tripped on the upgrade.

---

### Post by jswhite on 2008-04-27
Good news: The fix to my "hosts" file took care of the sudo issue. I can now successfully sudo from the command line. Thanks!

Bad news: Still no sound. Completing the fix from the Dell Wiki did nada for me. The modem driver had not renamed the sound driver and there were no old drivers to delete, so rebuilding initrd didn't really do much.

Phooey.

---

### Post by jswhite on 2008-04-28
Solved it by going [to this thread]("http://ubuntuforums.org/showthread.php?t=616845&highlight=hda+intel+alsa"). The Inspiron 1420n is not listed, but I found the driver I used and fiddled with the model settings. Eventually, I added in "model=dell-3stack", rebooted, and *poof*, I had sound back.

---

