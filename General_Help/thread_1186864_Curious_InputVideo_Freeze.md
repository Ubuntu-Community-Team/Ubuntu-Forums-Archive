---
title: "Curious Input/Video Freeze"
date: 2009-06-13
forum: General Help
---

### Post by austinjl on 2009-06-13
I hate to use my first post on this forum to ask a support question, but these freezes have become tiresome.

In multiple scenarios, the computer all-of-the-sudden freezes in this way:
-Screen remains the same
-Mouse moves
-No reaction to any input

I SSH into this laptop from another machine, and no process stands out as being stuck. I kill things without effect. I check the log files (dmesg, xorg, etc.) and nothing stands out. I restart GDM from SSH and nothing changes. "shutdown -r now" and everything's good as new.

I checked the known issues, and none of these seem to match my situation. I thought at first it seemed like this freeze occurred with Firefox running. I stopped using Firefox, and it still ocurred. I thought maybe it was the video driver. So I changed the default xorg conf to use vesa, and then FBDev; no change.

I really don't know what else to try or look at. Any ideas? Thank you.

-----

Here is a workaround that I've been using for the past week that works.

After coming out of suspend, I go to tty1 (Ctrl + F1), login as root, and run "/etc/init.d/gdm restart". I don't experience any of these freezes so long as I do this every time.

---

### Post by austinjl on 2009-06-18
So it froze just a few moments ago. I opened a SSH connection, and I noticed there were two instances of gdm running. I killed the first one, and nothing changed. I killed the second one, and the screen changed to black with green and purple lines. I hit the power button, and the the Ubuntu shutdown graphic came up with the progress bar. Shutdown seems fine, and now I'm wondering if this gives any clue what I should be looking for. I checked the dmesg and debug log files before shutting down, and nothing stood out.

---

### Post by austinjl on 2009-06-19
Here is the ps -A output from another freeze that ocurred last night.

---

### Post by austinjl on 2009-06-20
I am noticing that I don't experience these freezes don't occur if I don't suspend this laptop. Even though Jaunty boots pretty fast, I very much prefer to suspend than boot each time.

One other note, I experience a hardware freeze if I use the vesa driver, but rarely the kind of freeze listed above, no matter if I suspend or not.

---

### Post by austinjl on 2009-06-28
These freezes also occur when I hibernate. If I don't suspend or freeze, the PC operates just fine.

Does the gnome session resume after suspend/hibernate, or is it restarted? I'm thinking it may be a workaround to restart GDM after coming back from suspend.

---

### Post by gyenius on 2009-06-28
I'm having the same problem. But for me it seems like its only when I open certain windows. Like say if I open Thunderbird it works fine then I go to compose a new email it freezes. It will sometimes continue working for a few more seconds and will sometimes garble the screen and then it just freezes except for the mouse. 

I can tell everything is still running because the hard drive and wireless lights are still blinking away. I have even tried to restart X with control-alt-backspace (yes I have reinabled it) but nothing happens. I end up having to hold down the the power button to reboot.

btw I was having the same problem with synaptic but I killed its settings and now it works fine. And I'm using a Acer Aspire 4530 laptop.

---

### Post by austinjl on 2009-07-09
gyenius,

When my freeze occurs, the screen does not get garbled at all. It stays exactly as it was, except I can still move the mouse.

Have you tried different video drivers?

---

