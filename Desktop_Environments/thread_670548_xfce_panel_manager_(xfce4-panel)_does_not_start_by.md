---
title: "xfce panel manager (xfce4-panel) does not start by default."
date: 2008-01-17
forum: Desktop Environments
---

### Post by lweel on 2008-01-17
Hello xubuntu users,
I have installed xubuntu and created two user account. On the second user account the xfce desktop starts completly by default including the panel manager.
For the first user account the xfce desktop starts without the panel manager.
How can I fix this? Is there a way to edit that users startup configuration files that will make the panel manager start by default.

Please advise, thanks in advance.

---

### Post by ahaslam on 2008-01-17
You can start it with the 'run program' menu entry & then log out, choosing to save the session. If this fails 'xfce4-panel' can be added in 'autostarted applications' under the settings menu.

---

### Post by lweel on 2008-01-19
Hello Ahaslam, thanks for you fast reply.

Starting the panel manager with "Run Program..." (Alt-F2) xfce4-panel does the job.
Logging of your session with the checkbox "Save session for future logins" checked, brought back a running panel manager on the next login at start up.

---

