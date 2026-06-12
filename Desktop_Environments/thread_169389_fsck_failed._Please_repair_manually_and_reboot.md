---
title: "fsck failed. Please repair manually and reboot"
date: 2006-05-02
forum: Desktop Environments
---

### Post by icarusfall on 2006-05-02
On the bootup sequence, I'm now getting the above message after it forces a check.

"fsck failed. Please repair manually and reboot"

I'm really not sure what to do. If fsck failed, how can I repair the filesystem manually. Can anyone tell me what logs to check in order to solve this problem, please? I'd really be very grateful. I'm not really a linux expert, although I've been tinkering with Ubuntu for about six months now.

I'm running Ubuntu Breezy Badger, it's actually on an AMD64 system, but I was presuming that wasn't really relevant. I have two hard drives in the machine, one of was the main installation partition, and the other is a media partition on the filesystem. Can anyone tell me where to start?

Thanks

---

### Post by icarusfall on 2006-05-02
Sorry everyone, problem solved. (Although still not sure why problem happened).

I ran fsck -ACV -r
The output wasn't very helpful, but once it had finished running, and the machine was rebooted, it all seemed to be fine.

Well, maybe this will help out someone else. But if not, sorry to have wasted everybody's time.

---

