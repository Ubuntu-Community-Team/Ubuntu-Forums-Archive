---
title: "save the currenty xterm sessions in the workspace after reboot"
date: 2010-06-02
forum: Desktop Environments
---

### Post by bidon15 on 2010-06-02
Hi there, 
 
Need help - Anyone knows how to save the currently workspace settings on my desktop when logout/reboot/shutdown the old setting will resume? Currently, i have configured the multiple xterm sessions and placed them in each corner of workspace on dual monitors, but after the system rebooted the xterm sessions are resumed, but they display on one monitor instead of two monitor and overlapped each other. 
 
I followed to save the desktop setting at in the "startup Applications preferences\remember currently runnign application". This would not work as i wish. Littlery, i want each xterm session reopen and place in each corner of workspace(i have 20 xterm opened everytime -If someone knows to tweak it that would really appreciate it very much).
 
I run Ubuntu 10.04 LTS with daul monitors.
 
Thanks in advance,
 
DP

---

### Post by chrisstankevitz on 2010-07-27
I understand your xterm windows open in the wrong position when you log in.

Just be thankful you get anything... when I log in, I get nothing but a blank desktop.

Question: How do you get the xterm windows to reappear when you log in (albeit in the wrong position)?

Chris

---

### Post by chopinhauer on 2010-07-27
> **bidon15 said:**
> 
I followed to save the desktop setting at in the "startup Applications preferences\remember currently runnign application". This would not work as i wish. Littlery, i want each xterm session reopen and place in each corner of workspace(i have 20 xterm opened everytime -If someone knows to tweak it that would really appreciate it very much).
 

If you use **xterm**s you are effectively lucky to get anything at all. Switch to **gnome-terminal**, which communicates correctly with the session manager.

You will also be able to see the registered session in the ~/.config/session-state directory.

---

