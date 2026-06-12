---
title: "Quick Fix for Blank Desktop, Unity Vanished"
date: 2011-11-02
forum: Desktop Environments
---

### Post by u2nTu on 2011-11-02
This Compiz Configuration Settings Manager (ccsm)-related disturbance happened to me a few days ago and I wanted to post the quick fix for others who may be stricken with it.

Symptom:
Unity Launcher and Panel disappear after logout or reboot following use of ccsm

**_[COLOR=Red]DON'T[/COLOR]_:**

[LIST]
[*]Panic
[*]Get angry and uninstall 11.10
[*]Uninstall ccsm (most important)
[/LIST]

**_[COLOR=DarkGreen]DO[/COLOR]_:**

[LIST]
[*]Ctrl-alt-t to open a terminal
[*]Run 'ccsm' again
[*]Navigate to Preferences
[*]See that Profile is 'Default' (If gibberish, pick the other one.)
[*]Be sure Backend is GConf Configuration Backend (not Flat File)
[*]Goto Plugin List tab and uncheck 'Automatic pulgin sorting' and confirm
[*]Under 'Disabled Plugins', pick 'unityshell'
[*]Hit right-arrow to move it over to 'Enabled Plugins' column
[*]Exit ccsm
[/LIST]
After a logout or reboot, Unity should be back.

It is known that ccsm is currently buggy, but most features do work. My first reaction after the experience ("No such bug-riddled program shall remain on my system!") was to uninstall. It's now back and I look forward to updates fixing the bugs.

---

### Post by ian.d.rossi on 2011-11-05
Thank you! This post really helped me. Here is what happened with me to help others out.

My problems started while I was trying to change the key bindings for Scale and Preferences > Backend was already set to Gcon. I used your solution and changed Backend to Flat file and then back again. Although enabling the unityshell plugin is probably what fixed it.

p.s. You should correct the typo: 10.11 > 11.10

Ian

---

### Post by u2nTu on 2011-11-07
@ian.d.rossi, Thanks for the note (glad to be of help) and noticing the typo, now fixed.

Threw this together for post #15 of [this thread]("http://ubuntuforums.org/showthread.php?t=1873679"), which I found too hilarious to pass up.
[ ]("http://ubuntuforums.org/showthread.php?t=1873679")

---

### Post by mefumofu on 2011-11-07
Thank you so much for sharing this, you just lowered my stress level a ton!

---

