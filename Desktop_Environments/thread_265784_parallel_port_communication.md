---
title: "parallel port communication"
date: 2006-09-26
forum: Desktop Environments
---

### Post by alsm.asga on 2006-09-26
Hi

I cannot access the parallel port. I'm using ELDK to transfer data to a fpga, but I can't do it as a common user (only works as root). I've changed permissions (chmod 777) of /dev/lp0 , /dev/parport0 and also added the common user to the groups lp , lpadmin , tty, dialout . I took a look at  [http://www.vmware.com/support/ws5/doc/ws_devices_parallel_configure_linux.html#wp1064410](http://www.vmware.com/support/ws5/doc/ws_devices_parallel_configure_linux.html#wp1064410) but it still not working. Bellow, the error message that appears when I try to run ppc-linux-gdb -x script as a common user:


GNU gdb Yellow Dog Linux (5.2.1-4b_4)
Copyright 2002 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "--host=i386-redhat-linux --target=ppc-linux".
MPCBDM version 1.2.3 / 2001/10/25
unable to get access rights for printer port 0 addr 0x378..0x37A
error on opening printer port 0
cmgr_mb.init:327: Error in sourced command file:
Failed to connect to target 'mpcbdm'


Can anyone help me?

Thanks in advance

---

