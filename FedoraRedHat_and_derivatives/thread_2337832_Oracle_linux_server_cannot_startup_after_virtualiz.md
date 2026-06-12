---
title: "Oracle linux server cannot startup after virtualized"
date: 2016-09-21
forum: Fedora/RedHat and derivatives
---

### Post by kimminhnguyen on 2016-09-21
Hi everyone,

I did virtualization my physical machine which isrunning under Oracle linux server 6.4. Then I created virtal server on Virtualbox, howerver my Oracle linux serer could not startup. I did the following steps to vitualize:
- Convert physical machines by VMware Vcenter Converter Standalone client 5.5.3. Export it to vmdk files.
- Create virtual machine on Virtualbox 5.1.2, then start Oracle Linux server 6.4.
Oracle Linux Serer could not startup.
Note that I'm successful when runing these vmdk file on VMware ESXi.

Pls see error.

    ```

    00:00:12.659303 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=1 CmdIf0=0xc4 (-1 usec ago) CmdIf1=0xc4 (-1 usec ago)
    00:00:12.659425 PIIX3 ATA: Ctl#0: finished processing RESET
    00:00:12.664687 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0xc4 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
    00:00:12.664801 PIIX3 ATA: Ctl#1: finished processing RESET
    00:00:12.880628 PIIX3 ATA: LUN#0: disk read error (rc=VERR_VD_VMDK_INVALID_FORMAT iSector=0x960a0 cSectors=0x8)
    00:00:12.883083 PIIX3 ATA: LUN#0: disk read error (rc=VERR_VD_VMDK_INVALID_FORMAT iSector=0x960a0 cSectors=0x8)
    00:00:12.893981 PIIX3 ATA: LUN#2: disk read error (rc=VERR_VD_VMDK_INVALID_FORMAT iSector=0xbca20a0 cSectors=0x8)
    00:00:12.895059 PIIX3 ATA: LUN#0: disk read error (rc=VERR_VD_VMDK_INVALID_FORMAT iSector=0x960a0 cSectors=0x8)
```

If you need more information, pls let me know.
Pls help me.

---

### Post by howefield on 2016-09-22
Thread moved to the "*Fedora/RedHat and derivatives*" forum.

---

