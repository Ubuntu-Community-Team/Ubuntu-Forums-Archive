---
title: "[SOLVED] &amp;quot;Authentication Failed&amp;quot; when restarting X server"
date: 2008-10-20
forum: Desktop Environments
---

### Post by ddarsow on 2008-10-20
I have my computer (8.04) set to auto log in. It works fine, but for some reason if I try to restart the X server [ <Ctrl><Alt><Backspace> ] I get the message "Authentication Failed" and have to turn off the power to reboot the machine.

Any thoughts?

---

### Post by ajgreeny on 2008-10-20
What happens if you log-out and log back in, rather than just restart the xserver; do you get a login prompt then?

---

### Post by ddarsow on 2008-10-20
The problem has now escalated. I can no longer log in at all. When I restart the machine I get the same :Failed to Authenticate" error message.

Is there some way to resolve this from either the live CD or from the prompt in recovery boot?

_________EDIT____________

Problem solved. I booted to the live CD and, based on a combination of an educated guess & sheer dumb luck, navigated to the **/etc/pam.d/** directory and opened the **gdm** file located there. I then commented out the last line of the file (which I had added a while back). The line I commented out reads: **@include common-pamkeyring**.

If anyone has similar issue after enabling the common-pamkeyring, this may be a good place to start. What seems odd is that everything worked fine for several months.

---

### Post by stefgro on 2008-11-02
Thank you. I have had this problem for a long time, but commenting out the "@include common-pamkeyring" line in /etc/pam.d/gdm worked!

Thank's again.:popcorn:

---

