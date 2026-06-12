---
title: "CPU stays at 100% for no aparent reason"
date: 2006-08-18
forum: Desktop Environments
---

### Post by nahtical on 2006-08-18
I've searched this, but didn't see any threads really relevant to my problem. I'm using the latest 686 kernel with SMP (it's a Pentium 4 3GHz with HyperThreading). According to the 'System Moniter' utility, my CPU is always at 100%, with the 1st 'CPU' (from the HT obviously) ocassionally dropping down to like 90% for a second. None of the processes seem to be taking up all the CPU cycles though. The laptop's 2 fans are constantly spun up, so it seems to match what the system moniter is reporting. This isn't a problem under Windows XP, and the fans don't spin up if I'm not doing anything, so I assume that this has something to do with the GUI maybe?. It also seems fairly quiet during boot, and it's at the login screen that it seems to start working on something. I've got XGL/compiz installed, but it does it under both GNOME and XGL/compiz. I hope that's enough info, I will gladly provide more if needed.

---

### Post by Senshi on 2006-08-18
Something has to be using the CPU power.  Do you have something like BOINC installed?

---

### Post by Mau on 2006-08-18
What's the output of ```
top
``` in the terminal?

---

### Post by xp_newbie on 2006-08-18
Could this be related to the [Alt + Print Screen]("http://ubuntuforums.org/showthread.php?t=197911") problem?

---

### Post by nahtical on 2006-08-18
Well I ran top, and sure enough BOINC was sucking up all the resources. Wonder why it didn't show up on the system manager? I thought I had uninstalled it, but a check of Synaptic showed I indeed still had the client installed. Must of been the manager or something that I got rid of. But problem solved =). (This is why I love the ubuntu forums. I get up to eat dinner, sit back down, and I already have 3 responses ^_^)
Thanks all,
Ethan

---

### Post by johnrh on 2006-11-18
I hope it's ok to reactivate this thread with what is really a follow-up question. I see several users have diagnosed boinc as the 100% cpu culprit, but can't find anywhere giving a solution.
After some fiddling about with my boinc 'account' settings I set the 'max cpu usage' to 80% in the 'general' and 'home' prefs, and now when I startup I see under messages: General prefs from einstein@home and General prefs using separate prefs for home. So I assume that this is being correctly read by boinc-client.
But top shows boinc still hogging at 100%. Does anyone know how to make this setting effective in Edgy? Is it possible?
Thanks for any help.

---

