---
title: "Gnome 3.6 problems - I want to remove Gnome"
date: 2012-10-27
forum: Desktop Environments
---

### Post by PrinceNo1 on 2012-10-27
Hello, i installed Gnome 3.6 from synaptic package manager after a clean install of Ubuntu 12.10. Now i have serious issues in my system. For one, i can't shut down my computer and many programs (ie firefox) does not run at all. I get crash reports at every system start. I can log out but it doesn't let me to select any  desktop other than Gnome 3.6. This is kind of fresh installation, i only installed Gnome over it. Can i remove this new Gnome or replace with an older version (with less problems)? Thank you

---

### Post by Frogs Hair on 2012-10-27
The Gnome Shell can be removed but all desktop shells on 12.10 run on top of Gnome 3.6.  Does Ubuntu appearer in the login screen ?

Gnome 2 is no longer supported and 10.04 is the lasted supported version of Ubuntu to use it and reaches EOL in April .

---

### Post by PrinceNo1 on 2012-10-29
Hello again and thanks for the response. I managed to uninstall gnome  3.6 after a couple of system crashes and lots of code typing. But now my  system does not boot into graphical desktop directly. It boots to tty1  black screen and i need to manually boot into desktop by typing ```
sudo service lightdm start
```
Is there a way to automatize this? i dont want to type codes everytime to boot desktop.

---

### Post by PrinceNo1 on 2012-10-29
Never mind, i did some research and removed/re-installed stuff and now everything works like a charm. I have AMD Catalyst 12.11 beta drivers installed and working too. Thanks for the response, problem solved :)

---

