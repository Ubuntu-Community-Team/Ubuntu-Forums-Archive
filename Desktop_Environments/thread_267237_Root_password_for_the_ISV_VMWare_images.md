---
title: "Root password for the ISV VMWare images?"
date: 2006-09-28
forum: Desktop Environments
---

### Post by antheo on 2006-09-28
Hi,

I downloaded the Ubuntu 6.0.6 VMWare image from [http://isv-image.ubuntu.com/vmware/](http://isv-image.ubuntu.com/vmware/) to start playing with Ubuntu.

I figured out that the default user's password is ubuntu but the root password is not root. Would you know what is it?

Thanks, 

Antheo

---

### Post by x64Jimbo on 2006-09-28
Sounds silly, but the root pw and the user pw are one and the same, aren't they?

---

### Post by antheo on 2006-09-28
Believe me i tried this one too before posting. :-)

[FONT="Courier New"]ubuntu@ubunto:/$ su root
Password: (i typed ubuntu)
Sorry.[/FONT]

---

### Post by x64Jimbo on 2006-09-28
Well root doesn't have a password in Ubuntu. It's a disabled account. You have to sudo everything. 
Try 
sudo su
ubuntu

---

### Post by antheo on 2006-09-28
weird I typed "sudo su" and it made me root without asking for a password.

Thanks anyway!

---

