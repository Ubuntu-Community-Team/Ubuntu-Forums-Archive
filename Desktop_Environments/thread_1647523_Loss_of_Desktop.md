---
title: "Loss of Desktop"
date: 2010-12-17
forum: Desktop Environments
---

### Post by Alpha99 on 2010-12-17
Hi Guys 
Came across a broken link during updating system (Python) 
So I came across advise which i followed and though i had fixed the problem by removing the broken (python) Only to find i no longer have access to the Desktop.

This is what i have done so far_
booted to Recovery 
Logged in as the user.
Ran the following to reinstall desktop:-    
sudo apt-get install ubuntu-desktop

all seem well, but now it wants conf. so i have ran the following after rebooting:
 
sudo dpkg --configure -a

but still no joy, as when the system reboots it stops at the splash screen desktop  ubuntu
and seem to be trying to boot to the desktop. But no joy.

Anything more to do.
I would be grateful for your help here.

Thanks

---

### Post by Krytarik on 2010-12-17
This should restore a default "xorg.conf".
```
sudo dpkg-reconfigure --default-priority xserver-xorg
```

---

### Post by Alpha99 on 2010-12-18
> **Krytarik said:**
> This should restore a default "xorg.conf".
```
sudo dpkg-reconfigure --default-priority xserver-xorg
```

Thanks Krytarik
I have ran this command 
# sudo dpkg-reconfigure --default-priority xserver-xorg

returns with pkg: conflicting action -e (--control) and -r (--remove)

Type dpkg --help about installing and un-installing packages 
[*];
Use 'deselect' or 'aptitude' for user-friendly package management;
etc etc

Options marked 
[*] produce a list of output - pipe it through 'less' or 'more' !
:~$

Still no go, after reboot, is there something i might have missed here.

---

### Post by Krytarik on 2010-12-18
To check if the xserver is installed, what is the output of:
```
dpkg -l | grep xserver-xorg
```

---

### Post by Krytarik on 2010-12-18
Is there a xorg.conf in place right now?

If so, rename it, e.g.:
```
sudo mv xorg.conf xorg.conf.backup-18.12.2010
```
Then again try to
```
startx
```

---

### Post by Alpha99 on 2010-12-18
> **Krytarik said:**
> Is there a xorg.conf in place right now?

If so, rename it, e.g.:
```
sudo mv xorg.conf xorg.conf.backup-18.12.2010
```Then again try to
```
startx
```

Ran as requested - results read

sudo mv xorg.conf xorg.conf.backup-18.12.2010

:cannot start 'xorg.conf' no sutch file or directory


------------------------------------------

Not able to post results as too much to copy over - but as to earlier request :-
dpkg -l | grep xserver-xorg
list from  xserver-xorg           1.7.5.*6-0ubuntu3
               xserver-xorg-core  2.1.9.0-0ubuntu7

to 
             xserver-xorg-video-voodoo  1.1.2.4.0-0ubuntu1
Totaling 40 Xserver listings.

Ok.

---

### Post by clrg on 2010-12-18
He meant /etc/X11/xorg.conf of course. You need to cd there first.

---

### Post by Alpha99 on 2010-12-18
> **clrg said:**
> He meant /etc/X11/xorg.conf of course. You need to cd there first.

Sorry.

Ok 

i have now cd etc/X11
ls -l

16 items listed 

I cannot see any reference to xorg.conf         listed here.

---

### Post by Krytarik on 2010-12-18
Please do this:
```
sudo apt-get update
sudo apt-get upgrade
```
If you are getting any errors then do this:
```
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
```
If that was succesful then again try:
```
sudo dpkg-reconfigure --default-priority xserver-xorg
```

---

### Post by Alpha99 on 2011-03-20
> **Krytarik said:**
> Please do this:
```
sudo apt-get update
sudo apt-get upgrade
```If you are getting any errors then do this:
```
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
```If that was succesful then again try:
```
sudo dpkg-reconfigure --default-priority xserver-xorg
```

To solve problem Needed to do a new install and on a different machine  - no problem.
All is now well

---

