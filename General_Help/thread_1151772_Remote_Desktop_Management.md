---
title: "Remote Desktop Management"
date: 2009-05-07
forum: General Help
---

### Post by s1mp13m4n on 2009-05-07
Hello everyone.  I want to control a WinXP machine from my Ubuntu 9.04 machine.  In a nutshell I want to be able to perform maintenance on the WINXP machine from my Linux machine.  The computer is in the kitchen and mine is in the bedroom and they are networked via a wired router.  I am new to this, so how would I go about doing this?  I know there are Windows options for this and I could do this using my WinXP partition but I would rather stick with and use Linux.  Thank you for the help.  :)

---

### Post by kanikilu on 2009-05-07
Is remote desktop enabled on the Windows XP computer? If not, first enable it by going to Start > right-click My Computer > Properties > Remote tab. 

Then from Ubuntu you can use rdesktop (CLI) or tsclient (GUI) to log into the computer remotely. All you should need is the hostname or IP address of the XP computer.

---

