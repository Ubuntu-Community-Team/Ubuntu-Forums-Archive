---
title: "root password"
date: 2005-12-16
forum: Desktop Environments
---

### Post by JoeRotonda on 2005-12-16
Installed ubuntu 5.10 but can only signon as user...system install never asked for or told me the root passord.?? help anyone.?

I got the cd at a LEAP meeting..

Joe Rotonda

---

### Post by teaker1s on 2005-12-16
use 'sudo' or 'gksudo' before command to gain root access eg 
sudo synaptic 
gksudo nautilus
root account is disabled for security if you want terminal as root 
'sudo su'

---

### Post by yanik on 2005-12-16
there are no root passord, you are supposed to use sudo instead.  

If you really want root, type sudo passwd.  it will ask your user password, then prompt you for a new UNIX password for root.

---

### Post by earobinson on 2005-12-16
please see [My FAQ]("http://earobinson.blogspot.com/2005/12/earobinsons-ubuntu-faq-how-to-solve.html") Question 1 (one and only question right now)

---

