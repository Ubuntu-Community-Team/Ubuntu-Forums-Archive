---
title: "can't login and login screen menu missing"
date: 2007-11-21
forum: Desktop Environments
---

### Post by Antikx on 2007-11-21
After a reboot I was unable to login to X windowsI (but I can log into a tty).
At the GUI login I get the popup window "Authentication Failed" for every user on the system.

so I logged into a tty, killed gdm and ran:
```
startx -- :1
```
that got me into X windows...

One of the last things I did before this problem started was change the login screen to the one with the actual people standing in a circle. On the first reboot I saw the people standing in a circle but couldn't login ("Authentication Failed" error). So I powered down and pulled the battery from my laptop. From then on I still had the "Authentication Failed" error but now my graphical login screen was a simple blue theme. I also no longer see a way to change the login screen theme from the System -> Adminstration menu. The link to the Login screen Setup application is no longer in the menu!

I've tried using aptitude to reinstall gdm and some of the pam stuff but it hasn't helped.

Any ideas, please?

EDIT1: I should also add that when I click the shutdown button on the top right, I no longer see the option to shutdown or reboot.
EDIT2: I attached the error message I got when logging into Xwindows using the "startx -- :1" command

---

### Post by Antikx on 2007-11-21
At a frieds recommendation, I checked the /var/log/auth
```

Nov 21 14:24:10 montanaqL-67769 gdm[5351]: PAM (gdm) illegal module type: -e
Nov 21 14:24:10 montanaqL-67769 gdm[5351]: PAM pam_parse: expecting return value; [...session]
Nov 21 14:24:10 montanaqL-67769 gdm[5351]: PAM unable to dlopen(/lib/security/required)
Nov 21 14:24:10 montanaqL-67769 gdm[5351]: PAM [error: /lib/security/required: cannot open shared object file: No such file or directory]
Nov 21 14:24:10 montanaqL-67769 gdm[5351]: PAM adding faulty module: /lib/security/required

```
Looks like a problem with PAM?
Any suggestions?

---

### Post by Antikx on 2007-11-22
problem solved
I had run alien on some Novell RPM's to get a novell client working and I 
think it messed up my gdm PAM file when I installed them.
I had a friend send me a known working PAM gdm file and I was able to fix mine 
up.

---

