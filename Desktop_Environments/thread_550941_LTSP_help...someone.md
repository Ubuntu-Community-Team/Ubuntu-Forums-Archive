---
title: "LTSP help...someone?"
date: 2007-09-14
forum: Desktop Environments
---

### Post by bazz on 2007-09-14
I am trying to use windows 2003 as a dhcp server with ltsp. I followed this [https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP)
but have  no luck. The tftp keeps timing out when the client boots. 
I can get the pxelinux.0 file if I do it from term. like this
tftp
get
/ltsp/i386/pxelinux.0

However the thin client at boot just times out.

can anyone please help me.

---

### Post by bazz on 2007-09-14
never mind again. it was a nic problem. I though the nic would work because it did with the LTSP's DHCP, but when doing DHCP from win2003, the nic does not work with pxeboot.

---

