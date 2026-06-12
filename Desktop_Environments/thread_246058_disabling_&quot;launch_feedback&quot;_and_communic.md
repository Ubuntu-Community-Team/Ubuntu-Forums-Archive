---
title: "disabling &quot;launch feedback&quot; and communication problem with kcontrol"
date: 2006-08-28
forum: Desktop Environments
---

### Post by arvs on 2006-08-28
Launch feedback is the feature with the bouncing icon next to the cursor and the temporary entry in the taskbar. It doesn't work properly on my system (often goes on for 15 seconds after the process has completed, while Xorg is using up 10 % or more extra cpu time).

So I want it disabled, which is possible by ticking off the option on every entry in the KDE menu. But i'd like to do it system-wide, which seems to be possible from the KDE Control Center. I tried ticking off the options at Appearance & Themes -> Launch Feedback. But this did nothing for me. 

The options are registered with the Control Center because when I load it again it shows the options changed. This is probably due to a communication error because when I do 

$ sudo kcontrol 

it says 

ERROR: Communication problem with kcontrol, it probably crashed.

but starts up fine afterwards.

Does anybody know either a way to solve the problem with the control center or another way to disable the launch feedback? Thanks in advance.

---

### Post by Denta on 2006-11-07
Experiencing identical problems :S

---

### Post by m666 on 2007-02-04
```
$ kcontrol
```
(without 'sudo')

---

