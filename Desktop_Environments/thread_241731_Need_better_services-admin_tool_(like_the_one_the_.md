---
title: "Need better services-admin tool (like the one the help file shows)"
date: 2006-08-22
forum: Desktop Environments
---

### Post by ChipA on 2006-08-22
We're very frustrated by the simplistic services-admin tool that is provided in the 6.06 release.  It only shows a limited subset of the services that are installed, it doesn't allow you to start/stop/restart services immediately, it doesn't allow you to change service startup order, etc.  Yes, all that can be done by the command line, but the services-admin GUI should also support it.

We were even more confused when we clicked the "Help" button for the services-admin tool.  Lo and behold, the help system describes the exact functionality we are looking for.  It even has a screenshot of our miracle tool!  Some more digging revealed that the tool is available at [http://www.gnome.org/projects/gst](http://www.gnome.org/projects/gst).  But that version isn't in the Ubuntu repositories.  ](*,) 

Being somewhat new to Debian, we are reluctant to just download the latest GST tarball and slam into some directory.  So we're left with several questions:

1.) Should we report the incorrect help information as a "bug"?
2.) Anyone have any idea when this newer version of services-admin will be officially available?
3.) Anyone have any idea of the "safe" way to install this newer version into 6.06?  (Preferably one that uses Synaptic or apt-get in some way.)

Thanks in advance for your help,
Chip

---

### Post by amohanty on 2006-08-23
GUI based:
**sudo apt-get install bum**
System->Administration->Bootup Manager

Terminal Based:
**sudo apt-get install sysv-rc-conf**
In terminal: **sysv-rc-conf**

HTH
AM

---

