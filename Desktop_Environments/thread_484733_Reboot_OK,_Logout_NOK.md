---
title: "Reboot OK, Logout NOK"
date: 2007-06-26
forum: Desktop Environments
---

### Post by undecidable on 2007-06-26
Problem:
Clean install of Kubuntu 7.04 on a test IBM TP21.
If I try to just logout, it won't relogin.

But the following all work:
a.  I can reboot this machine with no problem,
b.  Using ctrl-alt-bspc performs a relogin with no problems.
a.  I have a copy of Ubuntu 7.04 on a different partition with no problems,
ie on Ubuntu/Gnome logout/login works OK.  

So the problem is not with either the graphics card or with xorg.conf.

What happens:
After logging out,
1st I get the Kubuntu logo screen with a black progress bar
then flashing cursor on blank screen.
Any input is reflected on screen but doesn't seem to be processed,
eg c-alt-bspc, ctrl-c, ctrl-z

I have to change to tty1 (c-a-F1),
login as root and shutdown.

The system log shows the attached errors:
kdm		:0[5312]: IO Error in XOpenDisplay
kdm[5018]	Display :0 cannot be opened
kdm[5018]	Unable to fire up local display :0; disabling
but again these errors do not happen on re-boot.

Copy of DMesg is attached.  
The beginning is where I logout/login
(all prior to that has been deleted and refers to the previous boot)
The final section is after the (successful)  reboot. 

Question:  what is different between logging out/logging in and re-booting that would cause this error only on logging out/in?
Any assistance tracking this down appreciated 
as it is somewhat inconvenient not to be able to logout.

---

### Post by PaulFr on 2007-06-26
Have you seen this active bug (and the comment from Kevin Colyer for a possible workaround) ? **[https://launchpad.net/ubuntu/+source/kdebase/+bug/47455/comments/8](https://launchpad.net/ubuntu/+source/kdebase/+bug/47455/comments/8)**

---

### Post by undecidable on 2007-06-26
Just tried launchpad for the 1st time.
The bug appears to be known:
[https://bugs.launchpad.net/ubuntu/+bug/38915](https://bugs.launchpad.net/ubuntu/+bug/38915)

In the bug report there is a workaround for those with KDE:
adding the line:
TerminateServer=true
in the [X-:*-Core] section of the kdmrc-File (/etc/kde3/kdm/kdmrc)

and for those with Gnome:
in /etc/X11/gdm/gdm.conf
setting:
AlwaysRestartServer=true

The first workaround worked for me.

---

### Post by undecidable on 2007-06-26
re:
"Have you seen this active bug (and the comment from Kevin Colyer for a possible workaround) ? https://launchpad.net/ubuntu/+source...455/comments/8"

Paul

thanks.  I do have that bug (47455) also,
but it is not causing the problem I mentioned.  
The relevant bug for me at least is 38915.

---

