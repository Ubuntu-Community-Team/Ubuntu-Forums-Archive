---
title: "Weird video effect on notifyer and system-monitor"
date: 2009-11-02
forum: Desktop Environments
---

### Post by drumbug1 on 2009-11-02
Please see the attachment.  This is on a clean install of Xubuntu on a Compaq Evo N600c laptop.  There is currently no xorg.conf file (I've read this is a new feature in Karmic).

Has anyone else seen anything like this?  I've only noticed it on the notifier and the System Monitor.  Everything else seems to be working fine.

---

### Post by pokepasa on 2009-11-03
I have the same problem on a Compaq Evo N1020v, exactly the same.
 
The graphic card is an ATI Radeon IGP 340M (maybe this can help?).
 
I have tested it on clear installation and live CD. In Ubuntu 9.10 it does not happen.
 
Anyone can help?

---

### Post by drumbug1 on 2009-11-03
Interesting.... so system-monitor works fine if you're using GNOME?  I'll have to give a Ubuntu 9.10 live CD a shot and see if I have the same result.

---

### Post by spacecheck on 2009-11-03
> **drumbug1 said:**
> Please see the attachment.  This is on a clean install of Xubuntu on a Compaq Evo N600c laptop.  There is currently no xorg.conf file (I've read this is a new feature in Karmic).

Has anyone else seen anything like this?  I've only noticed it on the notifier and the System Monitor.  Everything else seems to be working fine.

Please see my two responses in this thread and try the suggestion:
[http://ubuntuforums.org/showthread.php?t=1305279&highlight=system+monitor+notices&page=2](http://ubuntuforums.org/showthread.php?t=1305279&highlight=system+monitor+notices&page=2) 
Might solve the problem immediately.
Ciao

---

### Post by drumbug1 on 2009-11-03
> **spacecheck said:**
> Please see my two responses in this thread and try the suggestion:
[http://ubuntuforums.org/showthread.php?t=1305279&highlight=system+monitor+notices&page=2](http://ubuntuforums.org/showthread.php?t=1305279&highlight=system+monitor+notices&page=2) 
Might solve the problem immediately.
Ciao

Hi spacecheck.  This is XFCE, not GNOME (see thread title), so your last post's suggestion to 
> try turning on "Normal" effects on the "Visual Effects" Tab under the Menu item: System\Preferences\Appearance instead of "None"?"
..doesn't apply because that is a GNOME-specific control panel.  I definitely think this looks like the same issue, so if anyone knows how to make the same change without installing GNOME, please let me know.

Thanks!

---

### Post by mcmunt on 2009-11-03
I have this exact problem in 9.10 under Gnome on an IBM R40 laptop. It also uses an ATI Radeon video card. My [thread]("http://ubuntuforums.org/showthread.php?t=1312300") has no comments . .  yet.

You're not alone :)

---

### Post by pokepasa on 2009-11-03
By the way, I put a [thread]("http://ubuntuforums.org/showthread.php?t=1312527") too with my issue and 2 printscreen.
 
No responses yet.

---

### Post by mcmunt on 2009-11-03
Pretty much solved for my IBM R40 with ATI Radeon [here]("http://ubuntuforums.org/showthread.php?t=1312300"). Change of acceleration type in xorg.conf shows the notifications and System Monitor normally but Xorg seems to use a bit more CPU.

---

### Post by pokepasa on 2009-11-04
The problem is that in my Xubuntu there is not xorg.conf file.
 
And, for what I read in this links, the change affect so much the performance. Maybe the best is wait for a patch?

---

### Post by bburg on 2009-11-04
> **pokepasa said:**
> I have the same problem on a Compaq Evo N1020v, exactly the same.
 
The graphic card is an ATI Radeon IGP 340M (maybe this can help?).
 
I have tested it on clear installation and live CD. In Ubuntu 9.10 it does not happen.

Exactly the same problem with my N1020v using 9.10 Gnome. I had no problems with 9.04.

---

### Post by bburg on 2009-11-04
Problem solved by modifying /etc/xorg.conf. See [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001/comments/13](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001/comments/13)

---

### Post by pokepasa on 2009-11-05
> **bburg said:**
> Exactly the same problem with my N1020v using 9.10 Gnome. I had no problems with 9.04.
 
Surprise for me!!! Have you tested the Live CD of GNome? Im suposing Gnome=Ubuntu.
 
I say it because I've tested the Ubuntu 9.10 Live CD in my N1020V and this problem does not happened.

---

### Post by pokepasa on 2009-11-05
Well, finally I've read this [link]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1304635&page=2") and I can have a xorg.conf file and configure it to solve the problem.

---

### Post by bburg on 2009-11-05
> **pokepasa said:**
> Surprise for me!!! Have you tested the Live CD of GNome? Im suposing Gnome=Ubuntu.
 
I say it because I've tested the Ubuntu 9.10 Live CD in my N1020V and this problem does not happened.
I mean Ubuntu 9.10 with the Gnome window manager. I haven't tested it with the Live CD. I did an upgrade from 9.04.

---

