---
title: "Help! grub error 24"
date: 2009-03-05
forum: General Help
---

### Post by jamesholl on 2009-03-05
I have Ubuntu 8.10 on a dual boot with windows, though each on different hard drives. I thought I'd give Fedora a try, and decided to install it. I opted to resize the Ubuntu partition to allow space for Fedora, and chose the "other" boot loader when asked. Now, I can't boot into anything, all I get is "error 24" from Grub loader 1.5
I've seen some mention of this problem out there, but nothing I can actually understand. Help me boot into my Ubuntu, please!

---

### Post by skymera on 2009-03-05
Boot the Ubuntu LiveCD and reinstall GRUB.

Fedora might have wiped it out.

When in LiveCD

```

grub 
```
```

find /boot/grub/stage1
root (hdx,x)
setup (hdx)

```

Type that into the LiveCD terminal.
Replace device with YOUR ubuntu drive
replace (hdx,x) with whatever "find" shows :)

That should reinstall grub and you should be able to boot.

---

### Post by jamesholl on 2009-03-05
Thanks skymera, 
I actually just did a reinstall of ubuntu itself on a separate partition, and since the new installation is able to access all the documents and stuff on the old ubuntu, it seems there's no harm done. But boy was I nervous for a while there, even going into BIOS, etc. 
But thank you so much anyway!!
james

---

