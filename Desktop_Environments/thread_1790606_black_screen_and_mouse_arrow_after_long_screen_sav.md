---
title: "black screen and mouse arrow after long screen saver shutdown"
date: 2011-06-25
forum: Desktop Environments
---

### Post by hanansela on 2011-06-25
HI
I have recently installed 11.04 natty on Intel Core  i3-2100 3.1 GHZ using its own graphic accelerator. When the screen is idle for a long time, more than 1 hour, I get a black screen with the mouse arrow but nothing else. the mouse moves the cursor and Ctl+Alt+F1 does work.   
How to fix this problem?
How do i get my screen back using Ctl+Alt+F1?
Thank you

---

### Post by jfieser on 2011-07-11
I have exactly the same problem on a Compaq Presario 2100 laptop.  After no activity, the screen goes blank, the mouse moves and the Cntrl-Alt-F1 lets you log in via text, but the X Windows is still black.

---

### Post by wildmanne39 on 2011-07-11
> **jfieser said:**
> I have exactly the same problem on a Compaq Presario 2100 laptop.  After no activity, the screen goes blank, the mouse moves and the Cntrl-Alt-F1 lets you log in via text, but the X Windows is still black.Hi,have a look at this link.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by wildmanne39 on 2011-07-11
> **john88online said:**
> It takes a long time to shut down and start my computer.What is the reason ?Is it for virus or another reason?
Hi, you should start a thread of your own with a good title, you do not have the same problem as the OP. I doubt it is a virus. open log file viewer and see what the dmesg log says.

---

### Post by hanansela on 2011-08-19
Hi
I have solved my problem changing the settings in system>preferences>power management>on AC power>display=never.
i do not know if it is the right thing to do but it works, i have no freeze of the screen after the computer has been idle for a long time.

---

