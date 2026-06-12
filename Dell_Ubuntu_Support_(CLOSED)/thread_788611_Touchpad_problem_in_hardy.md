---
title: "Touchpad problem in hardy"
date: 2008-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tylersontag on 2008-05-09
I've had a post or two about this but i think i'm nearing a solution.  My touchpad worked fine prior to installing hardy then she went out.  I talked to dell support, did a few things but to no avail, and it ended with "We don't support hardy yet"  But he did recommend i DL the live CD and see how it works on that.

I did so, and on the Live CD of hard my touchpad works fine.  So i sent over the xorg.conf file and tried saving it over my xorg.conf file on my hard drive.  Rebooted but still didn't work

So my question is, what other sources should i look at on the live CD to compare to my HD's files to figurte out whats different?

---

### Post by tylersontag on 2008-05-10
bump, anyone? i know theres just like 2 more files, i just don't know where they are or which they are. Im running a dell inspirion 1525n.

---

### Post by fragos on 2008-05-10
I have a USB cable connected touchpad which lsusb identifies as 0488:0020 Cirque Corp. In hardy it works without any configuration. I found 2 packages you can try for touchpad configuration that may help you, tpconfig and gsynaptics. My Dell 1420n is still running 7.10 and the plaptop touch pad is configured with a section in xorg.conf.

---

### Post by tylersontag on 2008-05-26
bump, any ideas?  Any files other than my xorg.conf that i should port over?

---

