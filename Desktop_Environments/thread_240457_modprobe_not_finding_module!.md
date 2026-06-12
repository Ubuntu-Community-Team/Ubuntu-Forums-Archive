---
title: "modprobe not finding module!"
date: 2006-08-20
forum: Desktop Environments
---

### Post by BlackBottle on 2006-08-20
Modprobe is not finding a module thats in its standard location.. insmod works. pls see the commands below.. any ideas will be helpful. thanks a lot!

/etc/modprobe.d> sudo modprobe cisco_ipsec
FATAL: Module cisco_ipsec not found.
/etc/modprobe.d> sudo insmod /lib/modules/`uname -r`/CiscoVPN/cisco_ipsec.ko
/etc/modprobe.d> lsmod | grep cisco
cisco_ipsec           546140  0

whats happening?

---

### Post by meng on 2006-08-20
Are you trying to use the Cisco VPN client? I found vpnc to be much easier to set up and use.
I know it doesn't answer your question, but I thought it worth mentioning ...

---

### Post by BlackBottle on 2006-08-20
thanks.. i'll try vpnc..
except that if that also needs some modules to be loaded at boot, i may run into similar issues

---

### Post by BlackBottle on 2006-08-23
doesnt anyone have any idea? i imagine this is such a basic thing, people would have come up with answers right away..

again, thanks in advance :)

---

