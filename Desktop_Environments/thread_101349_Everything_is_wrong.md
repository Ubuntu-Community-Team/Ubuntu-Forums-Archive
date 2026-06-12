---
title: "Everything is wrong"
date: 2005-12-09
forum: Desktop Environments
---

### Post by rashi on 2005-12-09
So I have been using Ubuntu for a few months and it has worked fine.  Well now nothing works, among other apps clock, trash app, nautilus, gnome session mgr, xine, well everytime now on my desktop will be half there, everything will ask if I want to restart it and then disappear, and then it asks me if i'd like to delete clock or trash, and it is all very this is too much and someone help please!

---

### Post by gruepig on 2005-12-10
This might be a long shot, since I'm sure what you're describing, but could it be that your mouse or mouse driver is misbehaving or misconfigured?  Like maybe when you click on something it's doing something other than you expect?

Do you have these symptoms when you first log in to gnome, or only when you use the mouse?

One other thing to verify would be whether you are having these problems in a non-graphical environment.  Hit ctrl-alt-f1 to get to a console.  Log in and run some commands.  (You might try dmesg and reading your logs, or upgrading your software with 'apt-get update && apt-get upgrade' or just running 'fortune' a few times for laughs.)  Basically, just do enough to see if you get any "weirdness".  You can get back to X/gnome with ctrl-alt-f7.

---

### Post by rashi on 2005-12-10
Well it is showing me the message:
EXT3-fs (device hda5) in start_transaction: Readonly filesystem

SO what does that mean and how do you fix it?

---

### Post by gruepig on 2005-12-12
Check the output of 'mount' or the contents of the file '/etc/fstab'.  You probably have something like '/dev/hda5 on / type ext3 (rw errors=remount-ro)'.  That means, mount the partition /dev/hda5 as writeable if possible, but if there are errors, remount it as read-only.  

So, this error message could be indicating hard drive problems.

Try rebooting.  If that doesn't fix it, try rebooting into single user mode (should be an option at boot) and running 'fsck /dev/hda5'.

---

