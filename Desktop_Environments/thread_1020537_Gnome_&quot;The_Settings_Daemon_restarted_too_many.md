---
title: "Gnome: &quot;The Settings Daemon restarted too many times&quot;"
date: 2008-12-24
forum: Desktop Environments
---

### Post by jcd2020 on 2008-12-24
Hi. I'm getting this very annoying message when starting gnome : 
There was an error starting the GNOME Settings Daemon. Some things such as themes, sounds, or background settings may not work correctly. The Settings Daemon restarted too many times. GNOME will still try to restart the Settings Daemon next time you log in.
The only visible error besides this message is that I can't mount drives with the places menu but I can with terminal. None of the solutions from this thread [http://ubuntuforums.org/showthread.php?p=3776732#post3776732](http://ubuntuforums.org/showthread.php?p=3776732#post3776732) helped. I'm running Ubuntu 8.04. All of this started after I removed and reinstalled the "damaged" libxi6 package with Synaptic in order to install perl-doc package and 30+ updates and packages required by it. Thanks in advance for any help.

---

### Post by s3gfault on 2008-12-24
sounds like the program is crashing whenever it is launched.  detailed error messages should be available in the system log, but i'm not sure where this program logs its output to.  Check the /var/log folder, or dmesg, for errors that may provide more information.

---

