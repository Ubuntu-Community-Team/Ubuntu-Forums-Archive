---
title: "X on acer aspire 1694 WLMi"
date: 2006-02-23
forum: Desktop Environments
---

### Post by a2m on 2006-02-23
after ubuntu boots and X win is going to start, suddenly there is only black screen on my display.
i installed ubuntu with acpi=off
my resolution is 1280*800
what should i do?
thankz very much!

---

### Post by christhemonkey on 2006-02-23
did you try pressing Ctrl+Alt+F1 to get to a terminal?
This should let you log in and reconfigure your x server.
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by a2m on 2006-02-23
yes i have already tried it...and again i only heard login screen sounds (drums sample) and again black screen...
:(

---

### Post by lo1 on 2006-02-23
before you boot  (pressing enter) you type

boot: linux vga=771 acpi=off noapic nolapic

I've an acer aspire too and it does really work

---

### Post by a2m on 2006-02-23
i tried it with vga=771 acpi=off noapic nolapic but it doesn't work..

---

