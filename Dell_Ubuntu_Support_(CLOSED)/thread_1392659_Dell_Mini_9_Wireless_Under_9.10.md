---
title: "Dell Mini 9 Wireless Under 9.10"
date: 2010-01-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cerin on 2010-01-28
I just install 9.10 on a Dell Mini 9. Everything seems to work great, except for wireless. The Network Manager applet is active, but it never shows any networks, even though I have another Ubuntu laptop showing several networks. The hardware drivers dialog doesn't list any proprietary drivers available. What remaining setup is required to get wireless working?

---

### Post by mikewhatever on 2010-01-28
Dell mini 9 should have a broadcom card, which needs a driver. 
[http://ubuntuforums.org/showpost.php?p=8090292&postcount=1](http://ubuntuforums.org/showpost.php?p=8090292&postcount=1)

---

### Post by Cerin on 2010-01-28
Yeah, after I installed all the updates, the hardware dialog showed the Broadcom driver. However, I installed that and rebooted, but wireless still isn't working.

---

### Post by mikewhatever on 2010-01-28
Well, apparently, the dialog thing doesn't work in Karmic, at least not for Broadcom. Since you do have wired connection, just install bcmwl-kernel-source package, and it should work after a reboot.

---

### Post by Cerin on 2010-01-28
False alarm. Checking under "Preferences", I noticed it hadn't automatically detected my wireless eth2 interface. After filling that in, it connected perfectly.

---

