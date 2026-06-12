---
title: "Tweaking shutdown in Kubuntu"
date: 2007-07-05
forum: Desktop Environments
---

### Post by Mark Phelps on 2007-07-05
I, too, have this well-known shutdown problem in Kubuntu, and before anyone points me to the myriad of forum topics on this for a solution, let me tell you that I have spent the last three nights trying ALL of them.  I've modified /boot/grub/menu.lst so many times that I can practically do it my sleep.

My general results have been disappointing, as follows:
-- Linux hangs during use but shutdown from the KDE menu works OK
-- Linux doesn't hang during use, but shutdown from the KDE menu only work some of the time
-- Logging off from KDE and then choosing shutdown work some times but not others
-- and so on, and so on, and so on ...

What DOES work (all the time!) is entering "sudo shutdown now" from a terminal.  So, since that works, is there any way to tweak the shutdown options in KDE so that it will run that command when I press the the shutdown button?  (also, to do a similar thing with the Restart button).

---

### Post by aos101 on 2007-07-06
Do you have the problem in this bug report where it just hangs when you shutdown/restart?

[https://bugs.launchpad.net/ubuntu/+bug/38915](https://bugs.launchpad.net/ubuntu/+bug/38915)

If so I've found this fixes it: [https://bugs.launchpad.net/ubuntu/+bug/38915/comments/43](https://bugs.launchpad.net/ubuntu/+bug/38915/comments/43)

---

### Post by sparkymartin on 2007-07-07
I tracked my kubuntu (dapper LTS) shutdown issue to the splashscreens.  When the system did shutdown properly I noticed that the first shutdown msg was 'resetting the splash screen', so I deduced that might be the issue.  I dislike the splashscreens to I got rid of them.

_This is what I did:_
1. removed the splashscreen from being loaded by grub: replace 'splash' with 'vga=791  acpi=force' from /boot/grub/menu.lst (remember to backup the file first before editing)
2. Then I uninstalled any splashscreen apps that were installed, namely usplash & ksplash).

After that the system shuts down successfully every time, and never hangs.

---

### Post by secretkeeper81 on 2007-10-03
> **aos101 said:**
> Do you have the problem in this bug report where it just hangs when you shutdown/restart?

[https://bugs.launchpad.net/ubuntu/+bug/38915](https://bugs.launchpad.net/ubuntu/+bug/38915)

If so I've found this fixes it: [https://bugs.launchpad.net/ubuntu/+bug/38915/comments/43](https://bugs.launchpad.net/ubuntu/+bug/38915/comments/43)

Thanks! It seems to be working for me!

---

