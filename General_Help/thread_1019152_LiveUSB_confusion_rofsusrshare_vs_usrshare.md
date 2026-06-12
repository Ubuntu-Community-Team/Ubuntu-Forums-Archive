---
title: "LiveUSB confusion: /rofs/usr/share vs /usr/share"
date: 2008-12-22
forum: General Help
---

### Post by tescott on 2008-12-22
I was wondering if someone out there can help me clear up my confusion.  I'm encountering a problem with my timezone (/etc/localtime) getting reset on every reboot.  (I'm running Ubuntu off of a USB pen-drive.)

I have traced the problem down to:

/usr/share/initramfs-tools/scripts/casper-bottom/02timezone

This overwrites /etc/localtime with /root/usr/share/zoneinfo/UTC.  I went and modified this file to get rid of this operation.  However, it doesn't seem to correct the problem.  After looking further, I see this file:

/rofs/usr/share/initramfs-tools/scripts/casper-bottom/02timezone

I'm *guessing* that this is what is being used at boot and why the editing of the other 02timezone didn't correct my problem.  I can't edit the /rofs version of the file directly as /rofs is read-only.

So, my confusion lies in understanding why there's /rofs/... and /usr/....  Editing the /usr/.../02timezone is pointless if it is ignored.  So, what's the point of this existing in the first place?

Is there a way around this?  Do I need to follow the LiveCD customization in order to get my hands on the original 02timezone?  Can I somehow get the boot process to utilize my modified 02timezone instead of the /rofs version?

Thanks.

---

