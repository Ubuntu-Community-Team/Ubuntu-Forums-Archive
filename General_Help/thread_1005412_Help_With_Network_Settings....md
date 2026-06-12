---
title: "Help With Network Settings..."
date: 2008-12-08
forum: General Help
---

### Post by knightrider37876 on 2008-12-08
I am running a version of Ubuntu called "gOS". Whenever I try to use the GUI for my Network Settings I need to click the Unlock button in order to change the settings. When I click the Unlock button I am prompted for a password. I enter my password, but it does not accept it (the box shakes and wants me to retry the password). Any suggestions? Again, I'm just trying out the "gOS" software, but I'm having difficulties... This also happens when I try to change the system clock... :confused:

---

### Post by CrusaderAD on 2008-12-08
Try changing your password for root:

sudo passwd root

and then retry. Maybe your password is wrong?

---

### Post by knightrider37876 on 2008-12-08
Thanks for responding. I tried that, but still no luck...

---

### Post by CrusaderAD on 2008-12-08
What exactly are you trying to change? You could always do it from the command line.

sudo vi /etc/network/interfaces

---

### Post by knightrider37876 on 2008-12-08
I tried typing in the command 'neat', but it said "bash: neat: command not found".

---

### Post by linux6994 on 2008-12-08
gos is a fine OS, yet too locked down for my taste. Ubuntu straight up would be the better OS in my view.

---

### Post by knightrider37876 on 2008-12-08
Well, I thought about trying the straight-up new version of Ubuntu. However, I cannot get the LIVE cd to boot because of initramfs + busybox errors...

---

### Post by CrusaderAD on 2008-12-08
> **linux6994 said:**
> gos is a fine OS, yet too locked down for my taste. Ubuntu straight up would be the better OS in my view.

I agree. If you want those fancy "docks" like with the mac or gOS, you can always use simdock or something like it in the Ubuntu GUI.

---

