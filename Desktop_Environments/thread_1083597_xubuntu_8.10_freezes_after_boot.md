---
title: "xubuntu 8.10 freezes after boot"
date: 2009-03-01
forum: Desktop Environments
---

### Post by cllaudyu on 2009-03-01
after i upgraded from xubuntu 8.04 to 8.10 it started to freez during boot and needed to forcely reboot it every time

i had the same problem in kubuntu and ubuntu after it finished upgrading up-to-date

---

### Post by thtrgremlin on 2009-03-01
when does it freeze?

in grub, edit the line that has > kernel /boot/vmlinuz-2.6.27-7-generic ro silent splash -- and delete the "quiet splash" part so all it says it > kernel		/boot/vmlinuz-2.6.27-7-generic ro --

also, if there is a line at the end that says > quietdelete that line completely. Then press 'b' to boot.

This will give you a verbose startup where rather than having a loading screen, you can watch every little thing it is doing, or failing to do. If it freezes during startup, this will tell you exactly what it was doing when it froze.

And just to make things easier, restart at least 3 times to make sure it is always freezing doing the same thing.

Let me know what it is doing when it freezes, even if it isn't always in the same place.

And for the sake of argument, also check if it is possible to boot to recovery mode. Either way, sure we can track this down.

---

