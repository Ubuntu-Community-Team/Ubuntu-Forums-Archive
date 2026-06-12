---
title: "Printer queue locks after suspend"
date: 2005-12-02
forum: Desktop Environments
---

### Post by JohnnyV on 2005-12-02
My print queue seems to be locked after resuming from suspend. The jobs just sit in the queue until I reboot. Then they all print. I have looked for a way to get the jobs printing but no luck so far. Anyone know how to fix or work around this?

---

### Post by dcstar on 2005-12-02
[QUOTE=JohnnyV]My print queue seems to be locked after resuming from suspend. The jobs just sit in the queue until I reboot. Then they all print. I have looked for a way to get the jobs printing but no luck so far. Anyone know how to fix or work around this?[/QUOTE]
You may want to change your parallel port settings (assuming it is a parallel printer) in your BIOS and just experiment to find if there is a better setting.

---

### Post by JohnnyV on 2005-12-05
Thanks for the tip. There are not many options in the bios but I tried them. The queue still hangs after suspend. I've tried killing everything related to printing and then restarting cups. The only way to get the queue to print is to reboot.

I'm sure there is a lock file somewhere.

---

