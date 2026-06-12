---
title: "Screen lock on lid close / suspend / hibernate"
date: 2006-08-23
forum: Desktop Environments
---

### Post by rapha on 2006-08-23
Hi all,

when I close my laptop lid, suspend or hibernate it, the screen is locked upon resuming from either of these states. Is there a way to disable that?

Thanks for any hints you might have! :-)

Best regards,
Raphael

---

### Post by yopnono on 2006-08-23
> **rapha said:**
> Hi all,

when I close my laptop lid, suspend or hibernate it, the screen is locked upon resuming from either of these states. Is there a way to disable that?

Thanks for any hints you might have! :-)

Best regards,
Raphael

Open the gconf-editor and go to this key:
 /apps/gnome-power-manager/   here you have suspend and hibernate

lock_on_suspend
lock_on_hibernate

---

### Post by rapha on 2006-08-23
That worked like a charm, thanks a lot! :-)

---

