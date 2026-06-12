---
title: "Ubuntu Herd 2 - i386 Alternate CD - gdmsetup"
date: 2007-01-17
forum: Development CD/DVD Image Testing
---

### Post by ahaslam on 2007-01-17
OK a strange one...

I can't change the login settings using gdmsetup, this is from both the control center & the CLI.

When I issue 'gksudo gdmsetup' I'm asked for my password and then nothing happens, it just seems to wait indefinitely. 

This happens at every attempt, on every login - no errors are ever logged, it just waits :-k 

Hardware specs (if applicable) can be found in this post: [http://www.ubuntuforums.org/showpost.php?p=2021641&postcount=1](http://www.ubuntuforums.org/showpost.php?p=2021641&postcount=1)

I tried removing */tmp/.gdm_socket* & rebooting to no avail. Also worth noting is that there's no option for 'GDM Setup' at the login screen, is this intentional?

Tony.

EDIT: Submitted to Launchpad: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/80323](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/80323)

---

### Post by pochu on 2007-01-17
That's a known bug.

Here is the bug report with the upstream bug and the workaround:
[https://launchpad.net/ubuntu/+source/dbus-glib/+bug/71248](https://launchpad.net/ubuntu/+source/dbus-glib/+bug/71248)

But thanks for testing and reporting the bugs, and do it always you can!

Regards
Pochu

---

### Post by ahaslam on 2007-01-17
I can confirm that workaround, 'sudo dbus-launch gdmsetup' works for me ;)

Tony.

---

### Post by ahaslam on 2007-01-19
Any idea why I'm getting multiple emails regarding duplicates of the above bug, 80522 & 80601?

Tony [-(

---

### Post by pochu on 2007-01-19
No idea, I just receive one mail.

Open a ticket at answers.launchpad.net

---

### Post by Henrik on 2007-01-20
I've seen other people report multiple emails too. I expect someone is working on it. You can always ask about these kind of things on #launchpad on freenode too.

---

### Post by pochu on 2007-01-20
Yes, sometime ago I had that problem. But since then I just receive one mail per bug.

---

