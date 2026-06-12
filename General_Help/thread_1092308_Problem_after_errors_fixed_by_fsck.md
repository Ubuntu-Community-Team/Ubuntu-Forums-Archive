---
title: "Problem after errors fixed by fsck"
date: 2009-03-10
forum: General Help
---

### Post by bbabu84 on 2009-03-10
I have an Intrepid (Ubuntu 8.10) installation in which the disk gave problems when it was checked and I ran fsck manually (as suggested by the message) and there were a few stray blocks and block counts that were fixed.  When I try to boot the system now, I get a text login screen and not the graphical (gdm) screen.  I tried to run "startx" manually, but it runs for a few seconds and just returns the prompt.  Looking at the X logs don't reveal much.  Before I reinstall the system, do you have any suggestions on what I can try?  I am a fairly knowledgable Linux user (but new to Ubuntu) and a high-level suggestion on avenues to try would be appreciated.  Thanks.

BB

---

### Post by Peter09 on 2009-03-10
What version are you running, it looks like the system is intact but your x-server is not configured.

If you get a menu when going into recovery mode, choose the fix x-server option.

---

### Post by kryptikos on 2009-03-10
Hi Peter...without the X log file it is a little hard to troubleshoot. However sometimes X doesn't configure correctly on install and all it needs is a "little push" to reset and reconfigure itself. You can do this by booting up to your login (you said you were able to get to runlevel 3) and then either become root or run 'sudo' and this command:

**[INDENT]dpkg-reconfigure xserver-xorg[/INDENT]**

That will run you through an 8 bit console graphic "wizard" to reconfigure X. See if that helps. It could be the sync frequencies got out of whack by choosing a resolution the card ultimately can't handle etc. Hopefully that will help a bit :)

---

### Post by bbabu84 on 2009-03-10
> **kryptikos said:**
> Hi Peter...without the X log file it is a little hard to troubleshoot. However sometimes X doesn't configure correctly on install and all it needs is a "little push" to reset and reconfigure itself. You can do this by booting up to your login (you said you were able to get to runlevel 3) and then either become root or run 'sudo' and this command:

**[INDENT]dpkg-reconfigure xserver-xorg[/INDENT]**

That will run you through an 8 bit console graphic "wizard" to reconfigure X. See if that helps. It could be the sync frequencies got out of whack by choosing a resolution the card ultimately can't handle etc. Hopefully that will help a bit :)


Thanks for the suggestion.  I will try to reconfigure xserver and see if it solves the problem.

BB

---

