---
title: "Xsession: Warning: Unable To Wite To /tmp"
date: 2005-10-22
forum: Desktop Environments
---

### Post by Brando569 on 2005-10-22
hey something very wierd just happened to my hoary installation. for about the past hour or 2 ive been trying to get a custom kernel to work with splashy/Upower. i made one and forgot to include FB support, so i was thinkin and was like "hey i could use the 2.6.12-12 kernel sources from the breezy repo and make a custom kernel out of that" so i did that and went through and checked all the options that i wanted, compiled the kernel, and installed it. i then rebooted my computer and i saw splashy for about 15 secs then it went to the "error: reverting back to console" and i saw errors about my partitions being mounted, but i couldnt read then cuz the font was really small and it went away too fast. is there a way to log your boot process to read logs that hoary made about the boot process? now onto my main problem: everything booted up fine (all other stuff and my needed partitions) and i got to KDM and tried to login and it said this:

Xsession: Warning: Unable to write to /tmp; X session may exit with and error.

and i clicked ok and it brought me back to KDM. i figured ahh stupid me i forgot to include support for tmpfs or sumthin like that. so i rebooted and went to the default hoary kernel and it did the same thing. i then booted into breezy (luckly i had installed breezy previously) and checked the permissions of /tmp and everything checked out. i then rebooted into hoary and it did the same thing. anyone have any idea of what going wrong and how to fix it?

---

