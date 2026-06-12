---
title: "Conveniency: Return to the same work environment after a reboot?"
date: 2010-08-30
forum: Desktop Environments
---

### Post by Leeteq on 2010-08-30
It would be great to be able to help spread Linux by helping others manage convenience such as automatic startup elements. I think it is important to find solutions that does not involve custom scripts, preferably something that can be done through the package manager or the like. "GUI" is important, even if done in simple ways with little options. (Related example on simplicity: The gui for "ufw" - the ubuntu firewall should be included and enabled in Ubuntu by default). 

In short - on next boot; **How to return to what you left?**

[LIST]
[*] **same mounts** (automatically) mouted (with same permissions)
[*]**same applications** (windows) open (in their respective workspaces)
[*] **same window transparency** (opacity) level as last time for each window
[/LIST]
 [B]
Volume mounts through reboots:[/B]
How to ensure the same effect as when manually mounting volumes with the user account (not root), while actually auto-mounting them on startup? (I have not found a way to make the fstab startup mounts accomplish this, as that is done by root and not by the user account.) The problem is that various different behaviours related to file and folder security permissions occur if mounted by root. For example; if I mount through fstab, the application launchers in my panels fail. If I mount manually with the logged-in user, the launchers start their applications just fine. As I know that "things work ok" when I mount them manually, I am looking for a way to set the system to mount them during startup with exactly the same effect. 

**Further on mounts and work environment:**

[LIST]
[*] Keep a clean desktop: how to hide all mounted drive icons from the desktop (show on demand, from another folder)? (some setting that prevents them from being placed on the desktop...) One reason; promote the wonderful world of window transparency (opacity) to allow editing documents with ultra-cool backgrounds without all sorts of icons cluttering the background image. This is actually a very practical addition to the bag of "cheap tricks" to inspire Windows users to try something "new". We know that Linux technically can match Windows for most people by now (some proprietary Windows-only software still cause headaches and limit the options), but it is harder to convince people with technical arguments; easier to show them enough eye-candy and obvious "quality-of-life" enhancing things to tempt them to give Linux a chance.
[/LIST]
 

[LIST]
[*] When putting a the 'mount' application launcher into a panel drawer, I also would like to choose which volumes to show (hide) in the mount list. It is practical to hide system partitions, recovery partitions, the potential dual-boot windows system partition, boot manager partition, backup partition, etc. etc. from non-technical users. But actually, also nice to have a short "most mounted" list to choose from even for immortals ;-).
[/LIST]
 
**Compiz workspace and window transparency (opacity) issues:**

[LIST=1]
[*] any way to "restore" each window's custom transparency level set through compiz manager on next system restart?
[*] any way to make each of the startup applications open in their previously "used" workspace/desktop? (not all crammed on workspace1 next time, but opens automatically where they were placed last time?) PS. The concern in this case only relate to the applications that starts automatically during boot.
[/LIST]
 
[CENTER] *These things can be important. We dont need "big spectacular" news to impress people with the power of Linux anymore, but rather just get rid of seemingly easy 'unnecessary' 'limitations' ('annoyances').*[/CENTER]

---

### Post by Old *ix Geek on 2010-08-31
Switch to KDE. Problem(s) solved. :D

---

