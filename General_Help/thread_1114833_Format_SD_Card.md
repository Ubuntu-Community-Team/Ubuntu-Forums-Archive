---
title: "Format SD Card"
date: 2009-04-03
forum: General Help
---

### Post by Earl_Maroon on 2009-04-03
I have an SD card reader built into my laptop that functions fine. SDs mount, unmount and file operations work well.

However, I need to format an SD and I can't select it in gparted. I don't know why this would be, and I don't know how to get around it. The SD seems to work normally, except on my NDS (which is why I want to format it). I have no access to other computers with SD readers.

Please might someone help me?


Edit: I have noticed that my SD doesn't show up in Nautilus when browsing as root. Could this be the issue?

---

### Post by Tobi-fp on 2009-04-03
Can you see it in gparted? you said you cant select it, does that equal not seeing it?

The easiest way would be to add it to /etc/fstab

---

### Post by Earl_Maroon on 2009-04-03
No, I can't see it in gparted.

I'll try adding it to /etc/fstab now.

---

### Post by Earl_Maroon on 2009-04-03
Editing fstab didn't help, but thanks anyway.

I did manage to format it though. I used ```
gksudo nautilus
```, then I found my SD card in /dev

I right clicked, selected "Open with other application...", typed in ```
gparted
``` and it worked.

I probably could have just used ```
gksudo gparted /dev/mmcblk0
```, which I tested and works.

---

