---
title: "Nautilus Crashes My Machine!"
date: 2008-05-19
forum: Desktop Environments
---

### Post by damonjablons on 2008-05-19
Hey Forumers,

I've tried to follow a bug report on this to no avail.  I'm pretty sure it's just some system configuration I have.  Nonetheless, it's extremely difficult to endure.

**Problem**: When I try to drag and drop files from Nautilus to the desktop, another instance of Nautilus, or another program such as Amarok for example, my system *completely crashes*.  I can't even use the key-combo Ctrl+Alt+Backspace to shutdown X.  I have to hold down the power button on my laptop and manually reboot in order to stop this problem.

Is there any way I can reinstall Nautilus?  Maybe there's another solution to this?

If not, how can I properly file a bug report when a stack trace can't be performed do to a full system crash?

Thanks in advance!
-D

---

### Post by VMC on 2008-05-19
> **damonjablons said:**
> ...
**Problem**: When I try to drag and drop files from Nautilus to the desktop, another instance of Nautilus, or another program such as Amarok for example, my system *completely crashes*.  I can't even use the key-combo Ctrl+Alt+Backspace to shutdown X.  I have to hold down the power button on my laptop and manually reboot in order to stop this problem.

Is there any way I can reinstall Nautilus?  Maybe there's another solution to this?

If not, how can I properly file a bug report when a stack trace can't be performed do to a full system crash?

Thanks in advance!
-DYes, Nautilus is in the synaptic manager so you can remove, update, reinstall.
But have you looked at your sys log files after rebooting or after power cycle? Anything in there to indicate the trouble.

---

### Post by damonjablons on 2008-05-19
How do I find my system log file?  Where is it located?

---

### Post by igster on 2008-05-19
There's a log viewer labeled "System Log" option under the System -> Administration menu.  The actual log files are located at /var/log

---

### Post by damonjablons on 2008-05-19
What exactly should I look for, and in which section should I look?

---

### Post by damonjablons on 2008-05-19
After a Nautilus reinstallation, everything is working normally.

Thanks for the help, this was killing me!

---

### Post by igster on 2008-05-19
Glad you fixed it!

FWIW, I searched around a bit and supposedly Nautilus creates a debug file in your Home folder named "nautilus-debug-log.txt".  Does that file exist in your home folder?  If it does I wonder if it contains any useful information.

---

### Post by damonjablons on 2008-05-19
> **igster said:**
> Glad you fixed it!

FWIW, I searched around a bit and supposedly Nautilus creates a debug file in your Home folder named "nautilus-debug-log.txt".  Does that file exist in your home folder?  If it does I wonder if it contains any useful information.

Actually, I don't have that file in my home folder.  Hopefully the problem is gone forever though.  Here's my guitar solo to celebrate: :guitar:

---

### Post by VMC on 2008-05-19
> **damonjablons said:**
> Actually, I don't have that file in my home folder.  Hopefully the problem is gone forever though.  Here's my guitar solo to celebrate: :guitar:The file is called ".nautilus" and you can only view it if you turn on "Show hidden folders".

---

### Post by damonjablons on 2008-05-19
actually in my home folder there is no ".nautilus" file.  the first thing i did was view the hidden files.

---

### Post by damonjablons on 2008-05-23
nope, the problem is back.  i take back my guitar solo.

---

