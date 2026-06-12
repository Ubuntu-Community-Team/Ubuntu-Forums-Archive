---
title: "Problem with USB stick!!"
date: 2009-01-09
forum: General Help
---

### Post by figgz on 2009-01-09
I am quite new to linux as a whole and am struggling with a new 16GB USB stick i have bought. 
When i connect the USB stick and go to COMPUTER > USB drive. and try to open it, I get "Unable to mount location - Can't mount file"... Can anybody help me with this problem???

---

### Post by LateNiteTV on 2009-01-09
try this as root:
```
mkdir /mnt/usbkey
mount /dev/sda1 /mnt/usbkey
```

your  usb stick should now be ready for use.****

---

### Post by hyperdude111 on 2009-01-09
On the left side menu choose the 16gb media and it'l mount, for some reason it wont work from the main nautilus.

---

### Post by figgz on 2009-01-09
> **LateNiteTV said:**
> try this as root:
```
mkdir /mnt/usbkey
mount /dev/sda1 /mnt/usbkey
```

your  usb stick should now be ready for use.****
bob@bob-desktop:~$ mkdir /mnt/usbkey
mkdir: cannot create directory `/mnt/usbkey': Permission denied
bob@bob-desktop:~$ mount /dev/sda1 /mnt/usbkey

Thanks for the reply but i put the command in and got the above back??

---

### Post by jsroth on 2009-01-09
You have to change to the root account by entering
```
su root 
```

Or use the commands LateNiteTV gave you with a 
```
sudo
```
in front of them.

---

