---
title: "Last upgrade killed Unity (bar and desktop disappeared)"
date: 2011-10-19
forum: Desktop Environments
---

### Post by dario7 on 2011-10-19
Hello everybody!
after I've installed the last upgrades no more unity bar and stuff for no apparent reason.
Thanks god I've Guake installed and I'm running my applications by command-line and ALT+F2. 

I've read somewhere to try this in terminal but didn't worked:
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

I'm pretty sure the problem is the upgrade, so I would like to roll back before the problems started with the "packet manager history" but I don't know which command should I type for run the Synaptic packet manager.

Anyone of you have the same problem?

---

### Post by Copper Bezel on 2011-10-19
You can't really roll back, but you don't need to panic. You're actually on the right track, but you're resetting the wrong gconf keys - Gnome Panel's keys don't correspond to anything in Unity.

Here, try _[this]("http://ubuntuforums.org/showthread.php?t=1863905")_.

---

### Post by Nysha on 2011-10-19
I must thank you for this, and also ask for a little more advice...

I've had a similar problem today on 10.04, with various GUI elements failing to load depending on the session type - occurred following updates, although I see that the suspect update is a Compiz thing which I don't believe exists under 10.04, so perhaps my case has a different cause.

In any case, I used the command posted by the OP in terminal under a GNOME session, which successfully fixed that session. This does at least mean that my netbook is now usable; thank God (and the OP!) for that, as it contains all of my university files and I have two exams next week. :)

However, this command failed to restore my Ubuntu Netbook Edition session to working order; the desktop menu still fails to load. I imagine that in order to fix that I need to modify the gconftool command, however I don't know how it should be modified. I would like to be able to use my familiar UNR session again, so I'd appreciate any help with getting the command right. :)

---

