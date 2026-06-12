---
title: "change how GRUB works without changing BIOS?"
date: 2009-05-06
forum: General Help
---

### Post by shortridge11 on 2009-05-06
Is there a way to skip GRUB and go to the first choice automatically unless you press a pre-defined key?  I just want to make my machine boot pretty fast.  Please don't say i should change the time it idles before choosing the first OS by default, it's the fact that loading GRUB doubles my boot time.

If this isn't possible, please let me know

---

### Post by LowSky on 2009-05-06
go to add remove, search for an app called start-up manager

it will install to system> admin > start-up manager

you can use that to change boot orders and to remove the timer

---

### Post by mcduck on 2009-05-06
You can't really ship Grub, it's the bootloader and not just a simple menu to select what to boot. You will need some bootloader to start the OS, for that grub is currently the best option.

If you just want to *hide* grub, that's of course possible. The suggested Start-up manager will allow you to do that but you can also just edit the /boot/grub/menu.lst file by hand and enable the "hiddenmenu" option.

Although this will not make any bigger difference in your boot speed than changing the menu timeout would. What ever you do, the minimum timeout is 3 seconds (as any less than that would make it rather annoying to try to select what to boot, or press the key in time to show the hidden menu).

If the time it takes for Grub to load the menu on your machine is longer than a second or two you of course have some problem with grub that can most likely be sorted out somehow. But if the menu loads quickly and you just want to make Grub to boot Ubuntu sooner the timeout is what you want to change.

---

### Post by CatKiller on 2009-05-06
> **mcduck said:**
> Although this will not make any bigger difference in your boot speed than changing the menu timeout would. What ever you do, the minimum timeout is 3 seconds (as any less than that would make it rather annoying to try to select what to boot, or press the key in time to show the hidden menu).

Actually, 1 second is fine. You can press the Esc key before you get the prompt if you want, and it'll still work. Or just spam the Esc key. But 1 second is plenty if time if you're expecting to have to press the button.

---

### Post by shortridge11 on 2009-05-06
the hidden option is exactly what i was looking for, many thanks

---

