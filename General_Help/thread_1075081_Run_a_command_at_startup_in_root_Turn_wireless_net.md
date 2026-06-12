---
title: "Run a command at startup in root? Turn wireless networks on?"
date: 2009-02-19
forum: General Help
---

### Post by jellylogix on 2009-02-19
I recently got my wireless adapter to finally work. And to initilize the driver and get the "Wireless Networks" thing to turn on, I had to run a command: 

sudo insmod rt2870sta.ko

Do you know how I can get this script to run everytime at boot, or possibly another way that I can get the Wireless Network part to turn on automatically. It's not visible or working, and in Restricted Drivers it says that the driver is installed but not in use until I run that command.

---

### Post by bodhi.zazen on 2009-02-19
Put > insmod rt2870sta.ko in /etc/rc.local

No need for sudo as that runs as root.

---

### Post by Triggerhapp on 2009-02-19
```
sudo gedit /etc/rc.local
```
Before the return 0 add any scripts you want to run as Root, I think these happen just before GDM.

Edit : aww, Ninja'd

---

### Post by Yellow Pasque on 2009-02-19
```
gksudo gedit /etc/modules
```
Add rt2870sta to the list

Either way should work. Note to self: type faster

---

### Post by Triggerhapp on 2009-02-19
> **Temüjin said:**
> ```
gksudo gedit /etc/modules
```
Add rt2870sta to the list

Actually Yeah, that makes more sense ;P

---

### Post by jellylogix on 2009-02-19
Thank you for such a quick reply. Nice to be able to get that out of the way before I lay down for the night. 

I used the first method, putting it in /etc/rc.local and it worked like a charm! Thanks again!

- Ryan

EDIT: I just tried the second method for kicks, and it works too! Thanks.

---

