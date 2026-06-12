---
title: "Reinstall GRUB"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Crypty on 2006-08-04
Hi, I had a problem with my boot managers. It would go to grub, then when i choose windows, it would load another menu to select vista or xp. I had gotten rid of vista a while ago though. In my attempt to remove the vista boot option, I booted windows in console mode and did a fixmbr and fixboot.

Now I don't get grub anymore, it just goes right into XP with no menu. How can I get GRUB to take over again?

---

### Post by cantormath on 2006-08-04
> **Crypty said:**
> Hi, I had a problem with my boot managers. It would go to grub, then when i choose windows, it would load another menu to select vista or xp. I had gotten rid of vista a while ago though. In my attempt to remove the vista boot option, I booted windows in console mode and did a fixmbr and fixboot.

Now I don't get grub anymore, it just goes right into XP with no menu. How can I get GRUB to take over again?

Did you try opening terminal and typing

```
$:\ sudo update-grub
```

---

### Post by r4ik on 2006-08-05
Try,

[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

or,

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Hope it helps,

Good luck !

---

### Post by Crypty on 2006-08-05
Got it. Thanks! :)

---

