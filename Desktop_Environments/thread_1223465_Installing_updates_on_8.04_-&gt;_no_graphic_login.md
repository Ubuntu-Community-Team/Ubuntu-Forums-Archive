---
title: "Installing updates on 8.04 -&gt; no graphic login"
date: 2009-07-26
forum: Desktop Environments
---

### Post by VadimRadionov on 2009-07-26
Hello,
  
 Yesterday i installed some proposed packages updates on 8.04 and today, trying to boot, the graphic login prompt fails to load. Everything starts as usual, the logo appears and the progress bar grows, then switches to text mode (lat line saying: "Running local boot scripts (/etc/rc.local) [OK]"). Then it tries to switch to graphics mode, but nothing appears and soon it falls back to text. This happens a couple of times.
  
Then the blue text screen appears saying: "The display serves has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0"
  
 How can it be fixed?
  
 Thanks you in advance,
  
 Vadim

---

### Post by VadimRadionov on 2009-07-26
syslog contains a sequence of pairs:

gdm[5825]: WARNING: gdm_cleanup_children: child 9049 crashed of signal 6
gdm[5825]: WARNING: gdm_cleanup_children: Slave crashed, killing its children
gdm[5825]: WARNING: gdm_cleanup_children: child 9201 crashed of signal 6
gdm[5825]: WARNING: gdm_cleanup_children: Slave crashed, killing its children
 ...



And the apt log contains some lines (that probably show errors)

debconf: unable to initialize frontend: Gnome
debconf: (DISPLAY problem?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
...
debconf: falling back to frontend: Readline

---

