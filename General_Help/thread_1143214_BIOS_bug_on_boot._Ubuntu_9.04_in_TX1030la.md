---
title: "BIOS bug on boot. Ubuntu 9.04 in TX1030la"
date: 2009-04-29
forum: General Help
---

### Post by elessar.telkontar on 2009-04-29
Hello Ubuntu Community!

I have a message in the boot of Ubuntu 9.04 that says:

```
BIOS bug local acpi#0 not detected
```

An then is some message that I can't read fully (because dissapears) that says something about a dummy acpi to emulate or something like that.

Now... The problem basically is this display because Ubuntu boots fine and the runs smoothly and nice. The message didn't appear on earlier versions (I have had installed 7.10, 8.04, 8.10 and never get that message). Additionally I have Vista and this works fine (not so fine as Ubuntu, jejeje)

My computer is a HP TX1030la with Ubuntu 9.04 and Vista.

---

### Post by spiderbatdad on 2009-04-29
I think you can get rid of this by adding nolapic as a boot option to the end of the kernel line in /boot/grub/menu.lst
not 100% sure. If you read through dmesg you might get a better idea.

---

### Post by cariboo on 2009-04-29
THe messages are due to the changes in the kernel, you may benefit from a bios update.

---

### Post by elessar.telkontar on 2009-04-29
my BIOS is up to date already, then what is happening?

---

