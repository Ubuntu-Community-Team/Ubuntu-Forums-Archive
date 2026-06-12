---
title: "lubuntu 18.04, cannot open apps from menu requiring superuser permissions."
date: 2018-10-29
forum: Desktop Environments
---

### Post by buzlite on 2018-10-29
I have upgraded to lubuntu 18.04 and have discovered that no application I activate from desktop menu requiring superuser permission can run.
Further research showed that 18.04 does not use gksu anymore. I'm assuming that this is the problem. Seems that lubuntu 18.04 uses lxqt-sudo instead.
Take for example. I cannot run synaptic from the desktop menu. But I can run it from console using $ sudo synpatic.
Could someone provide insight on how to fix this?
Thanks in advance.

---

### Post by again? on 2018-10-29
Do you see an authentication dialogue window or does it ask for authentication in the terminal when you run...
```
synaptic-pkexec
```

Is lxpolkit running?
```
ps aux | grep [l]xpolkit
```

---

### Post by buzlite on 2018-10-29
$ synaptic-pkexec
--This command asks for authentication in the terminal. When I enter my password, it give an error. eg...
> $ synaptic-pkexec
==== AUTHENTICATING FOR com.ubuntu.pkexec.synaptic ===
Authentication is required to run the Synaptic Package Manager
Authenticating as: myaccount,,, (myaccount)
Password: 
polkit-agent-helper-1: pam_authenticate failed: Authentication failure
==== AUTHENTICATION FAILED ===
Error executing command as another user: Not authorized

This incident has been reported.

> $ ps aux | grep [l]xpolkit
--this give no output
$ ps aux | grep polkit
root      1595  0.0  0.1 295888  9596 ?        Ssl  11:45   0:00 /usr/lib/policykit-1/polkitd --no-debug

---

### Post by again? on 2018-10-29
Don't use Lubuntu but have it installed along with some other desktops in a test partition.
I think lxpolkit should be installed a running.
If I uninstall lxpolkit, when I run **synaptic-pkexec** in terminal it will authenticate in terminal.
When lxpolkit is installed and running I get the authentication pop-up window.

Googling your "pam_authenticate failed" error I found this thread.
I haven't read through it but may be helpful.
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=841878](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=841878)

---

### Post by buzlite on 2018-10-30
I updated my system and all works fine.

---

