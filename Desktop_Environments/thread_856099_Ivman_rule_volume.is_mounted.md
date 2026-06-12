---
title: "Ivman: rule volume.is_mounted"
date: 2008-07-11
forum: Desktop Environments
---

### Post by l_b on 2008-07-11
Hi all,

I'm having a little problem with ivman.

I've created some ivman configuration that mounts my external harddisk. That works fine. Now I'm trying to run a script when a partition from that disk gets mounted. But when I plugin my disk, that second part doesn't work.

When I leave the disk in, kill ivman & restart ivman again it works!

Here's my config:

```
    
    <ivm:Match name="hal.volume.uuid" value="fde44609-8e13-4611-b3c4-ce52eb224f02">
      <ivm:Option name="exec" value="pmount $hal.block.device$ /media/usb_extern_1"/>
      <ivm:Option name="execun" value="pumount -l /media/usb_extern_1"/>   
    </ivm:Match>

    <ivm:Match name="hal.volume.mount_point" value="/media/usb_extern_1">
      <ivm:Match name="hal.volume.is_mounted" value="true">
        <ivm:Option name="exec" value="echo Test geslaagd 3 &gt;&gt; /var/log/ivman.log" />
      </ivm:Match>
    </ivm:Match>

```

Does anyone know what's wrong here? Thanks in advance!

---

