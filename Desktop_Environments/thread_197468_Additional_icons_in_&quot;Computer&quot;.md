---
title: "Additional icons in &quot;Computer&quot;"
date: 2006-06-15
forum: Desktop Environments
---

### Post by ozgur on 2006-06-15
I have noticed that there are some people who are having problems with additional icons in Computer, like hidden partitions or secondary "linux root volume". Here they are as I could find:

[http://ubuntuforums.org/showthread.php?t=192833](http://ubuntuforums.org/showthread.php?t=192833)
[http://www.ubuntuforums.org/showthread.php?t=186755](http://www.ubuntuforums.org/showthread.php?t=186755)
[http://www.ubuntuforums.org/showthread.php?t=190478](http://www.ubuntuforums.org/showthread.php?t=190478)

I have the same issue, it happened after upgrading to Dapper from Breezy. I have asked for help in another post but didn't get answer. Today I found out that there is a bug filled in at Launchpad about that.

[https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/47349](https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/47349)

So it looks like the problem is solved. But I have a question. I don't have that package mentioned in Launchpad. Do I have to download manually? Or isn't it ready yet? Sorry about that, I'm new around here and Linux :|

---

### Post by mlind on 2006-06-15
I think that package is called actually libgnomevfs2-0.
And that you must have installed.

---

### Post by ajfan on 2006-06-15
How do you install the update to fix this problem?

---

### Post by ortsanfang on 2006-06-16
I've updated my system, but this little problem is still there ... unfortunately.

---

### Post by regne v on 2006-06-16
Same thing [here]("http://www.ubuntuforums.org/showthread.php?t=197270").

Could you please test if running "sudo /etc/init.d/dbus restart" changes temporarily anything  as happened to me?.

Do an icon appear in the desktop when you mount an unmounted partition?.

Thx.

---

### Post by ortsanfang on 2006-06-16
regne v, 
etc/init.d/dbust restart removes temporarily the "second" root volume; I don't have any unmounted partitions. 

In my case the problem is this: I get two icons for my root partition - both icons "work" and show the same content.

---

### Post by ozgur on 2006-06-17
Dbus restart, temporarily corrected it, until a restart. Then they appeared again. But the thing is, if I check "volumes_visible" box for desktop, i only see the partition that is in fstab which i want to see. And in nautilus sidebar, everything is correct.
Today's update, installs new version of libgnome-vfs2. It removed "Linux / root drive" (or something like that) which was there besides "filesystem", but still my hidden "recovery" partition[not in fstab] and hda2 partition[noauto in fstab] is shown there.
So Computer doesn't read the fstab file? Any suggestions?

---

### Post by ozgur on 2006-06-19
Noone found out something yet? Looks like some other people are having the same problem too in Launchpad:
[https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/45330](https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/45330)
Any ideas?

---

### Post by Hi-Teck on 2006-07-12
If you are running a fresh install of Dapper, check and install the new updates that are available. After the reboot the problem with the duplicate drives in "Computer" will be fixed. At least this worked on both of my Dapper machines.

---

