---
title: "Can't log into desktop any more"
date: 2005-11-07
forum: Desktop Environments
---

### Post by don.fraser on 2005-11-07
I try to log in with name and password and have been able to for some time (love Kubuntu) but now it simply resturns me to the log in screen again. Passwords and username are all correct and work in terminal mode.
I've looked around the net and tried a large variety of things including uninstalling the kde desktop and reinstalling. Nothing seems to work. Please help as I am left with Fedora which sucks compared.

Thanks in advance

Don

---

### Post by mlomker on 2005-11-07
Have you tried Ctrl-Alt-F2 to go to a terminal and then at a prompt **startx**.  If it fails you'll at least see some error messages.  You could also try looking in /var/log/kdm.log

---

### Post by don.fraser on 2005-11-07
Yes - I should mention that the enlightenment desktop starts up ok. If I try startx kde I get a terminal window inside a background that looks a bit like the kde background but not and with nothing on it.

Fanx again

Don

---

### Post by asimon on 2005-11-08
If the startx trick and kdm.log doesn't produce some helpful error messages you could try to find some error messages in ~/.xsession-errors. Just log in (which will fail and returns you to the login screen again) and then Ctrl-Alt-F2 to a terminal and have a look at the log file .xsession-errors in your home dir. This is usually how I find out why my KDE log-in doesn't work.

Alternately you could try to login in "Failsave" mode, which will only give you a terminal windows but no window manager at all. From there just enter 'startkde',  error messages should then appear in the windows.

---

