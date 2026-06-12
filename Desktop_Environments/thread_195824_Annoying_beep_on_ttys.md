---
title: "Annoying beep on ttys"
date: 2006-06-13
forum: Desktop Environments
---

### Post by exclipy on 2006-06-13
My gettys (the terminals that show up on Ctrl-Alt-F1, etc.) emit an annoying beep every time I press enter or when I press Backspace too many times.  How can I turn this off?

---

### Post by exclipy on 2006-06-14
Bump.

---

### Post by kpkeerthi on 2006-06-14
System -> Preferences -> Sound -> System Beep (tab) -> Disable (checkbox)

---

### Post by kecci on 2006-06-14
[QUOTE=exclipy]My gettys (the terminals that show up on Ctrl-Alt-F1, etc.) emit an annoying beep every time I press enter or when I press Backspace too many times.  How can I turn this off?[/QUOTE]

You can "sudo rmmod pcspkr" and blacklist it by adding a line in /etc/modprobe.d/blacklist. This would actually remove any beep from your system.

---

### Post by exclipy on 2006-06-14
Thanks kecci, that one worked!

---

