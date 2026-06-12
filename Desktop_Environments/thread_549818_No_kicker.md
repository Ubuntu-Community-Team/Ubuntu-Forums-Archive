---
title: "No kicker"
date: 2007-09-13
forum: Desktop Environments
---

### Post by umuro on 2007-09-13
The kicker is not auto starting. One day it stopped starting. I have to call it from the console always.
$ kicker

When I call it manually, it is OK. I even tried to place it in ~/.kde/Autostart. But no use.

Who starts the kicker? What might be the reason for above?

---

### Post by linuxwizard on 2007-09-13
When you have your kicker up check settings on kicker to make sure you don't have it set to auto hide. Also have you tried moving mouse over the kicker and see if it pops up when hidden. One other thing are you using Amsn. I had problem with Amsn on my kicker I had to stop using Amsn and my problem stopped with my kicker.

---

### Post by umuro on 2007-09-13
No it's not auto-hide. It is not there really. I worked around by making a link in ~/.kde/Autostart finally. But I would not have to do that. Right?

(kicker is starting ok if I set its working directory to home).

---

### Post by merquer on 2007-11-03
same problem... running kubuntu 7.10, and kicker stopped autostarting and i have to launch it from the terminal every time

---

### Post by foof on 2007-11-14
I got the same problem just now! I played around, installing AWN, SuperKaramba and uninstalling them again. Don't know if that could be the cause of it? How do I get my kicker back?? (I run Kubuntu 7.10)

---

### Post by umuro on 2007-11-15
in "~/.kde/Autostart"
create a "Link to application". Rename it to "Kicker.desktop".
The command is "/usr/bin/kicker".
The working directory is "~" (your home folder).

This need not be done but it works until somebody finds the reason...

---

### Post by foof on 2007-11-15
I found the solution.
Just delete the file ~/.kde/share/config/kickerrc 
in your home directory and a new one will be created the next time you log in.
You just needs to configure it again as you want it.

Found it here:
[http://docs.kde.org/stable/en/kdebase/faq/panel.html](http://docs.kde.org/stable/en/kdebase/faq/panel.html)

/Andreas

---

### Post by suziequzie on 2007-12-07
> **umuro said:**
> in "~/.kde/Autostart"
create a "Link to application". Rename it to "Kicker.desktop".
The command is "/usr/bin/kicker".
The working directory is "~" (your home folder).

This need not be done but it works until somebody finds the reason...

Thank You!:KS I was getting very ticked off at always having to manually start kicker. This worked great.

---

### Post by umuro on 2008-01-16
Offical solution

```
sudo apt-get  kde-tweak
```
Now you a have a new section in KControl

```
kcontrol
```

Goto: KDE Components | The tweaK Applet | Panel

Check: Start Panel with KDE

---

### Post by emuman on 2008-04-17
I can't enable it. If I enable the checkbox, next start it's disabled. Same thing with the turn off restart buttons. I enable Offer, but next start it's disabled. How to get rid of this crappy tweak applet settings?

---

### Post by cyclops-user on 2008-06-01
I had the same problem, and using kde-tweak fixed the problem.

Thanks!

---

### Post by mse_uk on 2008-06-19
Thanks for this fix - I was pulling my hair out.

---

