---
title: "higher resolution on headless Ubuntu box"
date: 2009-03-25
forum: General Help
---

### Post by DiGiTY on 2009-03-25
i'm running Ubuntu 8.10 headless (no monitor) since i mainly SSH and VNC into it. the problem is if no monitor is connected it defaults to 800x600 all the time. i prefer 1024x768 for better viewing when I VNC in. how do i get it to do 1024x768 as defualt instead of 800x600?

---

### Post by Yashiro on 2009-03-25
Add vga=794 to the kernel line in your menu.lst.

> kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ba625896-3275-45ed-b485-da35aa123c61  ro splash vga=794

---

### Post by DiGiTY on 2009-03-26
Thanks for the reply.

I tried that and it didn't work (I added " vga=794" to the end of all four entries(including recovery and old kernels) just to be safe and nothing). It still displays at 800x600 when I VNC in and there's no options to go higher when I go to Screen Resolution.

Any other ideas?

---

