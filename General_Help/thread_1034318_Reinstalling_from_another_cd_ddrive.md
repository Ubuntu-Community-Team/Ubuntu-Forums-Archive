---
title: "Reinstalling from another cd ddrive"
date: 2009-01-08
forum: General Help
---

### Post by james.wilde on 2009-01-08
I have an old Dell Latitude D505 on which I am trying to install Ubuntu.  I know that the built-in cd drive is a bit faulty and I'm going to replace it.  In the meantime I have a usb cd drive which this machine can use but cannot access for installation at boot time.

Is there some easy way in which I can put the Ubuntu installation cd in that drive and have the system reinstall all packages that it originally installed so that I know they are in good form.  The cd has been checked for faults and has passed the md5 test.

Alternatively can I do the same thing from an iso image of the installation cd?  If so where should that image reside?

The hard disk is formatted with a slice for Ubuntu, a second slice which will be mounted as /home and a third slice with XP SP2 Pro.

Grateful for any advice.

//James

---

### Post by logos34 on 2009-01-08
Why not just reinstall?

I'd use Unetbootin. Get the windows version.

Copy the ubuntu .iso to your windows partition, then [follow this]("http://unetbootin.sourceforge.net/#install").

When you get to the partitioning section, point the installer to your separate /home. Like this:

[IMG]http://www.easy-ubuntu-linux.com/images/install-new-partition-mount-pts-final.png[/IMG]

---

### Post by james.wilde on 2009-01-09
Thanks Logos34, I'll give that a try.

//James

---

