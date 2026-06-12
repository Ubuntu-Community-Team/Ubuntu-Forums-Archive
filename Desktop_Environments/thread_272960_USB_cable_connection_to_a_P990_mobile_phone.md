---
title: "USB cable connection to a P990 mobile phone"
date: 2006-10-07
forum: Desktop Environments
---

### Post by aubergine on 2006-10-07
Hi

I'm trying to connect my SonyEricsson P990 phone in File Transfer mode. I keep geting:

mount: wrong fs type, bad option, bad superblock on /dev/sda,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so

When I do a dmesg | tail -20, I get :

[17199856.756000] end_request: I/O error, dev sda, sector 2
[17199856.756000] EXT2-fs: unable to read superblock
[17199856.772000] end_request: I/O error, dev sda, sector 16
[17199856.772000] ReiserFS: sda: warning: sh-2006: read_super_block: bread failed (dev sda, block 8, size 1024)
[17199856.776000] end_request: I/O error, dev sda, sector 128
[17199856.776000] ReiserFS: sda: warning: sh-2006: read_super_block: bread failed (dev sda, block 64, size 1024)
[17199856.776000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[17199856.792000] end_request: I/O error, dev sda, sector 16
[17199856.792000] ReiserFS: sda: warning: sh-2006: read_super_block: bread failed (dev sda, block 8, size 1024)
[17199856.800000] end_request: I/O error, dev sda, sector 128
[17199856.800000] ReiserFS: sda: warning: sh-2006: read_super_block: bread failed (dev sda, block 64, size 1024)
[17199856.800000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[17199856.880000] end_request: I/O error, dev sda, sector 0
[17199856.880000] XFS: SB read failed
[17199856.896000] end_request: I/O error, dev sda, sector 0
[17199856.896000] XFS: SB read failed
[17199856.920000] end_request: I/O error, dev sda, sector 64
[17199856.928000] end_request: I/O error, dev sda, sector 120
[17199856.944000] end_request: I/O error, dev sda, sector 64
[17199856.956000] end_request: I/O error, dev sda, sector 120


I'm not too sure what to do next - the device is shown on the Ubuntu File Browser.

Does anyone have any ideas on how to procede?

Thanks
Nick

---

### Post by lvanderree on 2007-01-17
update the firmware of the phone, that did the trick for me...

(or update to feisty, which has solved it by using a newer kernel, but I think the new firmware of the P990 is a better solution for now).

---

### Post by magicm73 on 2007-01-21
I have updated to the latest firmware but I have the same problems.
I would love to sync my Sony Ericsson P990 with Evolution.

Any solution?

---

### Post by lvanderree on 2007-01-21
I was only able to sync to opensync via SyncML, but this didn't go smoothly yet (2 months ago). When I have some time again, I will try to update OpenSync and try it again. I also read that horde should be able to sync, but also haven't had any time to try that out.

I haven't read anything about sync-ing via the cradle yet. I use the cradle to charge the battery and make data-connections.

---

