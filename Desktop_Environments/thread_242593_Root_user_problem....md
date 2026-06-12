---
title: "Root user problem..."
date: 2006-08-23
forum: Desktop Environments
---

### Post by namelkcip on 2006-08-23
This post refers to Kubuntu v6.06 - Dapper Drake

I have already read the Wiki and user guide, and I am aware of the fact that there is no root user.  I have been entering root mode when I need to via the "Administrator Mode" GUI button(s), and using sudo in terminal sessions.  However, when I attempt to enter Admin/root mode to edit my network settings (i.e. eth1) I am not granted access.  I am using the same user password that works in all other attempts.  I quickly see a message box pop up, but it is so fast I can't read it.  I am attempting to access this from the System->Settings icon on the task bar, as well as the Network Settings folder in Konqueror.  No rocket science needed, just wondered if I am doing something wrong, and/or if anyone else has had this problem.

Cheers,

Scott

---

### Post by mlind on 2006-08-23
> **namelkcip said:**
> This post refers to Kubuntu v6.06 - Dapper Drake

I have already read the Wiki and user guide, and I am aware of the fact that there is no root user.  I have been entering root mode when I need to via the "Administrator Mode" GUI button(s), and using sudo in terminal sessions.  However, when I attempt to enter Admin/root mode to edit my network settings (i.e. eth1) I am not granted access.  I am using the same user password that works in all other attempts.  I quickly see a message box pop up, but it is so fast I can't read it.  I am attempting to access this from the System->Settings icon on the task bar, as well as the Network Settings folder in Konqueror.  No rocket science needed, just wondered if I am doing something wrong, and/or if anyone else has had this problem.

Cheers,

Scott

I'm not Kubuntu user, so I don't know the name of the application that's launched by this applet. Try finding out it's name and launch it from terminal to see any error messages.

Does Kubuntu create file ~/.xsession-errors ? It usually contains helpful messages about warnings and errors.

---

### Post by namelkcip on 2006-08-23
Thanks for the reply.  I did not find any such error files, searching '/' for 'xsession*'  I am using the KDE Kontrol Panel, and the applet is launched by invoking 'kcmshell knetworkconfmodule'  When I launch this in a terminal window, I receive the error "Cannot connect to X server."

Scott

---

### Post by namelkcip on 2006-08-23
Here is the output from the terminal session:

root@Kbuntu:/usr/bin# kcmshell knetworkconfmodule
kcmshell: cannot connect to X server
root@Kbuntu:/usr/bin# kcmshell kcm_knetworkconfmodule
kcmshell: cannot connect to X server

Thanks,

Scott

---

### Post by mlind on 2006-08-23
> **namelkcip said:**
> Thanks for the reply.  I did not find any such error files, searching '/' for 'xsession*'  I am using the KDE Kontrol Panel, and the applet is launched by invoking 'kcmshell knetworkconfmodule'  When I launch this in a terminal window, I receive the error "Cannot connect to X server."

Scott

~/ refers to your $HOME directory. Try
```

tail ~/.xsession-errors

```

That error message usually means that DISPLAY environment variable is not correctly set, or application cannot find and connect X11 socket at /tmp.
Do other applications launched from terminal work normally?

Does kcmshell use/need root privileges?

---

### Post by namelkcip on 2006-08-27
Not sure if kcmshell needs root privileges, but I ran it from a "sudo -i" terminal anyways.

Scott

---

### Post by namelkcip on 2006-08-30
Problem solved.  Not sure what the root cause was, but I believe it had something to do with the X windowing system.  Some graphical password checks worked, but nearly all terminal sessions worked.  I came across a mini-HowTo that showed me how to update my /etc/sources.list file.  So I did that, and ran 'sudo apt-get dist-upgrade' followed by 'sudo apt-get install ubuntu-base' and finally 'sudo apt-get install kubuntu-desktop'  Following the hour or so to download, extract and install, all is working fine now...even better actually.

Thanks,

Scott

---

