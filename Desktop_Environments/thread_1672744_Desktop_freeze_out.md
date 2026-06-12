---
title: "Desktop freeze out"
date: 2011-01-21
forum: Desktop Environments
---

### Post by msknight on 2011-01-21
Odd situation this.

Ubuntu 10.10 - 64 bit. Updates are ... um ... up to date.

Periodically, like every fifteen to twenty minutes-ish ... the keyboard is frozen out and none of the pull down menus or task bar items respond. This is with the exception of some of the icons I've put in the top panel for the sysmonitor, etc.

All applications seem to continue running and everything operates, however I can't "move" any of the windows, Alt+Tab doesn't work and I can't switch virtual desktops. Fortunately I've got cairo-dock running so I can start/stop processes.  

The only easy way out of this is to switch to a TTY window for a few moments, and then switch back to the graphical window, then everything is back to normal for a few minutes more.


I've already done the, " System -> Preferences -> Startup Applications and added gnome-settings-daemon" in another thread and that hasn't done anything.

Recently, the only thing I've really done is change the visual effects to "extra", then VLC played up (a long standing, known problem apparently) and I lived with it for a few days, then switched it back to normal ... then I got fed up, wanted the graphical candy back so switched it back to extra again.

... but I'm at a loss as to what is causing this.

This is the last chunk from my syslog...
Jan 21 14:17:01 michelle CRON[6886]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 21 14:22:43 michelle acpid: client 1346[0:0] has disconnected
Jan 21 14:22:43 michelle acpid: client 1346[0:0] has disconnected
Jan 21 14:22:43 michelle acpid: client connected from 1346[0:0]
Jan 21 14:22:43 michelle acpid: 1 client rule loaded
Jan 21 14:22:43 michelle acpid: client connected from 1346[0:0]
Jan 21 14:22:43 michelle acpid: 1 client rule loaded
Jan 21 14:23:17 michelle kernel: [ 3116.327073] NVRM: os_raise_smp_barrier(), invalid context!
Jan 21 14:23:17 michelle kernel: [ 3116.336285] NVRM: os_raise_smp_barrier(), invalid context!
Jan 21 14:26:14 michelle kernel: [ 3293.531879] NVRM: os_raise_smp_barrier(), invalid context!
Jan 21 14:26:14 michelle kernel: [ 3293.542103] NVRM: os_raise_smp_barrier(), invalid context!
Jan 21 14:26:17 michelle kernel: [ 3296.047513] NVRM: os_raise_smp_barrier(), invalid context!
Jan 21 14:26:17 michelle kernel: [ 3296.058754] NVRM: os_raise_smp_barrier(), invalid context!

...and there are a lot of these in my messages....

Jan 21 14:23:17 michelle kernel: [ 3116.327073] NVRM: os_raise_smp_barrier(), invalid context!
Jan 21 14:23:17 michelle kernel: [ 3116.336285] NVRM: os_raise_smp_barrier(), invalid context!
Jan 21 14:26:14 michelle kernel: [ 3293.531879] NVRM: os_raise_smp_barrier(), invalid context!
Jan 21 14:26:14 michelle kernel: [ 3293.542103] NVRM: os_raise_smp_barrier(), invalid context!
Jan 21 14:26:17 michelle kernel: [ 3296.047513] NVRM: os_raise_smp_barrier(), invalid context!
Jan 21 14:26:17 michelle kernel: [ 3296.058754] NVRM: os_raise_smp_barrier(), invalid context!
Jan 21 14:28:51 michelle kernel: [ 3450.395265] NVRM: os_raise_smp_barrier(), invalid context!
Jan 21 14:28:51 michelle kernel: [ 3450.411569] NVRM: os_raise_smp_barrier(), invalid context!

---

### Post by msknight on 2011-01-21
I'm now getting a keyboard freeze out every couple of minutes. This is starting to drive me nuts. Seems to be at its worst while I'm using kmail. Anyone got any ideas please?

---

### Post by Krytarik on 2011-01-22
You are obviously running a proprietary Nvidia video driver. How did you install it?

To check if it's really video driver related, simply replace "nvidia" with "nv" in "/etc/X11/xorg.conf".

---

### Post by msknight on 2011-01-22
The driver was installed by the hardware symbol that popped up when the installation was run.

Here's the details.

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 210"
EndSection


It looked like it might have been akonadi having MySql trouble. Since reading some German forum (I don't speak German, which is what made it all the more incredible that I tried it) I installed MySql on the system and that seems to have stabilised it.

I worked it out because I was running Kmail (I don't use evolution, because it doesn't have a rule to forward mails ... I use that rule to forward important e-mails to my mobile phone) and one time I started it up without starting Kmail.

When I eventually started Kmail, it happened. A bit of digging, and this looks like what the fault is.

I'm keeping an eye on it, though.

---

### Post by Krytarik on 2011-01-22
Though it seems you have solved that particular issue, it would make sense anyway to save your current display/driver configuration to your xorg.conf, back it up before!:
- go to "System -> Administration -> NVIDIA X Server Settings"
- click at "X Server Display Configuration" on the left side
- check/choose your desired configuration
- click at "Save to X Configuration File"
- enter your "root"-password when asked
- choose replace, not merge!

---

### Post by fkruis on 2011-02-06
Hi, I noticed just today the messages appearing in my log
 and I was sure I had solved it before by loading another nvidia driver.
Checking back thru messages I found it started when update got new nvidia driver 270.18. So at this moment I'm reverting back to 260.19 hopefully that will solve it for now. It did not freeze anything just slowed it down here.

---

### Post by fkruis on 2011-02-06
Sorry but going back to version 260.19 did not stop the messages, so I have to find something else.:confused:

---

