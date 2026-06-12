---
title: "Problem with gdm"
date: 2009-11-25
forum: Desktop Environments
---

### Post by johnpsakas on 2009-11-25
I try to open gdm but i have a proble.
this appears
ioannis@ioannis-desktop:~$ sudo gdmsetup
[sudo] password for ioannis: 
** (gdmsetup:1706): DEBUG: init delay=30
** (gdmsetup:1706): DEBUG: Failed to identify the current session: Unable to lookup session information for process '1706'

** (gdmsetup:1706): WARNING **: Unable to find users: no seat-id found
** (gdmsetup:1706): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:1706): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:1706): DEBUG: adding monitor for '/home/ioannis/.face'
** (gdmsetup:1706): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:1706): DEBUG: Found 1 sessions for user ioannis
** (gdmsetup:1706): DEBUG: GdmUserManager: not adding session on other seat: /org/freedesktop/ConsoleKit/Session1

what's going wrong?

---

### Post by ib.lundgren on 2009-11-25
The gdmsetup in Karmic is not the same one as in Jaunty and lacks a lot of features that have not yet been implemented to match the new and rewritten gdm. Instead of features you will find a lot of unfixed bugs, one of which you are staring at =)

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/454420]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/454420")

---

