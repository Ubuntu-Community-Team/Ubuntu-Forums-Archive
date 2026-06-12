---
title: "Compiz  desktop crashes"
date: 2012-04-04
forum: Desktop Environments
---

### Post by osced on 2012-04-04
Since yesterday Compiz crashes regularly for me, sometimes it happens when I watch a video sometimes it happens when I surf on the web. I checked what kind of update I did yesterday and didn't find anything that I don't think can affect compiz more then the kernel update.

I tried to start with the old kernel but it didn't help, I also tried to reset unity & compiz and it didn't seem to help. I'm running Unity on Ubuntu 11.10 with a Nvidia GeForce GT 240. I hope someone can help me find out what my problem is.

Here is the latest log output when compiz desktop was crashing:
```
Apr  4 14:45:42 saced-desktop kernel: [ 1951.561326] do_general_protection: 24 callbacks suppressed
Apr  4 14:45:42 saced-desktop kernel: [ 1951.561333] compiz[1887]  general protection ip:2df9cd sp:bf8e0e80 error:0 in  libglib-2.0.so.0.3000.0[280000+f7000]
Apr  4 14:45:42 saced-desktop gnome-session[1812]: WARNING: Application 'compiz.desktop' killed by signal
Apr  4 14:45:42 saced-desktop gnome-session[1812]: WARNING: App 'compiz.desktop' respawning too quickly
Apr  4 14:45:42 saced-desktop gnome-session[1812]: CRITICAL: We failed, but the fail whale is dead. Sorry....
```The log output for other times is mostly the same, it's only the two first lines that sometimes changes.

//Osced

---

### Post by cbourbou on 2012-04-05
Hi

Am having similar problems, wanted to check whether I have matching log entries - in which log file (location) are your errors reported?

Cheers
Tino

---

### Post by osced on 2012-04-05
Hi

This log was from the syslog log entries.

//Osced

---

### Post by cbourbou on 2012-04-05
Aha - same entries, but the general protection in another lib than yours:

Apr  3 09:19:50 cbourbou-ch-l kernel: [  725.497542] compiz[2087] general protection ip:7f9d854d4a47 sp:7fffe93cea10 error:0 in **libunityshell.so**[7f9d85360000+225000]
Apr  3 09:19:50 cbourbou-ch-l gnome-session[2013]: WARNING: Application 'compiz.desktop' killed by signal
Apr  3 09:19:50 cbourbou-ch-l gnome-session[2013]: WARNING: App 'compiz.desktop' respawning too quickly
Apr  3 09:19:50 cbourbou-ch-l gnome-session[2013]: CRITICAL: We failed, but the fail whale is dead. Sorry....

Cheers
Tino

---

### Post by osced on 2012-04-05
I've got different lib some times, but don't think I got  libunityshell.so. So i'm not sure our problem is the same, but they are at least equal in some way. What have you tried to solve it?

//Osced

---

### Post by cbourbou on 2012-04-05
I've googled the error messages provided but didn't find anything conclusive, there are similar reported bugs, but as far as I understand (more towards end-user) - no remedy in (my) sight.

A couple of days ago, I've deleted .compiz* etc. as directed by "how to reset Compiz / Unity", but didn't help either.

At the time being, I'm living with the problem, 1-2 Unity crashes a day....

Cheers
Tino

---

### Post by osced on 2012-04-17
Now after some updates of Kernel and nvidia binary my problem seems to have disappear. How is it for you?

---

### Post by cbourbou on 2012-04-23
Hi - for me, the problem still exists. However, I have an Intel graphic card (i915 driver). I have a feeling that the problem *might* be related to the external LCD screen I use at work, since my session (yet) never crashed when I was working on the notebook, without external LCD.
Hope it will get better over time.....glad you're over the worst part :-)

---

### Post by cbourbou on 2012-04-23
After some more googling, found confirmed bug 920488, which reflects my error conditions (segmentation fault in Xorg log), and its the same hardware "*This is an integrated Intel graphics card from a Dell Latitude E6420*". Last entry from March 5th....

---

