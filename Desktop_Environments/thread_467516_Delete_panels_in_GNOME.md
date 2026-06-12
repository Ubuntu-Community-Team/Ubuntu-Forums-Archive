---
title: "Delete panels in GNOME"
date: 2007-06-07
forum: Desktop Environments
---

### Post by jfinkels on 2007-06-07
Is it possible to delete both panels in GNOME? The option to delete the last remaining one is greyed out.

---

### Post by NeoLithium on 2007-06-07
I believe that you have to have at least one panel active, though you can always just shrink it or make it hidden (Through transparency or other means.)

---

### Post by jfinkels on 2007-06-07
> **NeoLithium said:**
> I believe that you have to have at least one panel active, though you can always just shrink it or make it hidden (Through transparency or other means.)

I have it on autohide, with hidden size of 0, and unhide_delay of 2147483647 (the integer limit).

---

### Post by init1 on 2007-06-07
> **jfinkels said:**
> Is it possible to delete both panels in GNOME? The option to delete the last remaining one is greyed out.
No. Do you need them to be deleted or are you just curious?

---

### Post by jfinkels on 2007-06-07
> **init1 said:**
> No. Do you need them to be deleted or are you just curious?

Just curious.

---

### Post by mcduck on 2007-06-08
The only way to get rid of the last panel is killing the gnome-panel process. And, as it's configured to automatically restart when killed, you'd have to go to System/Preferences/Session and change it's style to 'normal' instead of 'restart'.

---

