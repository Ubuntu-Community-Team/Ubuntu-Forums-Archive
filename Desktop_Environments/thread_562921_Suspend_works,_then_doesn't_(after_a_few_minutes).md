---
title: "Suspend works, then doesn't (after a few minutes)"
date: 2007-09-29
forum: Desktop Environments
---

### Post by Greg T. on 2007-09-29
I'm trying to get suspend working and I'm tantalizingly close. It actually works if I resume within a couple minutes of going into suspend mode. However, if I wait more than a few minutes--say, ten minutes or so--when I come out resume I get the dreaded blank screen. Everything else seems to kick in; my case fans, printer and the rest all fire up when I come out of resume, but the screen stays blank.

I've turned off my screensaver and turned off various power management options that might have otherwise kicked in after a few minutes of inactivity, but it hasn't helped. I've also added the following to my xorg.conf file, to no avail:

```

Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection
```

Any suggestions on how to resolve or diagnose this? Given that I have to wait several minutes to see the problem, it's time-consuming to test this repeatedly. I need a little help here.

---

### Post by Greg T. on 2007-12-02
Still searching for an answer. This always occurs after suspend has been going for ten minutes.

Here is the relevant portion of my xset results:

> Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0

DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

I've checked xset both before and after entering suspend, and it gives the same result. I've also checked out my BIOS settings, but didn't see anything that would trigger this. My GNOME power management settings have been moved to "never."

I'm at a complete loss. Any help in diagnosing the problem would be appreciated.

---

### Post by Greg T. on 2007-12-02
Removing gnome-screensaver did the trick! Now if I could only figure out why it hangs on restart after a suspend....

---

### Post by DagMan on 2008-01-02
if you're certain that's the problem, try adding to your suspend scripts
gnome-screensaver-command -i &
and in somewhere in your resume scripts 
killall gnome-screensaver-command

and maybe you can still have your screensaver installed.  It sounds like your screensaver is coming on at resume before the video is up when it's been a lengthy suspend.

---

