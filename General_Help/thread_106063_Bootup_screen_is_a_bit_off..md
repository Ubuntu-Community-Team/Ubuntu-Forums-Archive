---
title: "Bootup screen is a bit off."
date: 2005-12-19
forum: General Help
---

### Post by howboring on 2005-12-19
Hi Guys!

I've finally got Linux running on my laptop! :p 

The only problem I'm having is that during the start-up sequence screen where it shows Ubuntu in the middle and it shows the different parts loading, the screen seems to be a bit low (vertically) so the words start appearing at the top! :???: 

But as soon as the Login section comes in. It's perfectly fine. My laptop screen resolution is 1024x768 which is correct.

Is there an easy fix for this? It's not really a big problem. But it's just nice to have it.. ermmm.... perfect :rolleyes: 

I'm new to Linux and I've only been playing with it for a week and I'm loving it :p 

Thanks!

Ken

---

### Post by Chris Tucker on 2005-12-19
whenever you start working with the CLi, this will give you a real pain.. 
sudo gedit /boot/grub/menu.lst

then add vga=773 to the end of your kernal boot line (theres only one per boot choice! dont add it to every line!)
this will give you a 256 color 1024x768 console.
there are other console sizes you can choose too, but this one seems fit for you, tis what i use. i had the same problem with my CLi.

---

### Post by howboring on 2005-12-19
Hi Chris! Thanks for the quick reply! :p 

Where do I add vga=773?

I'm sorry I'm new to this. Here is what I get:

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

---

### Post by Chris Tucker on 2005-12-19
at the end of each "kernel" line, except the memtest86 one.
i say all the linux kernal lines because that overlap, will royally get on your nerves should you ever need to use a recovery mode.. speaking from experience.

---

### Post by howboring on 2005-12-20
Thanks Chris! It worked! :p

---

### Post by Chris Tucker on 2005-12-20
No problem :)
Merry Christmas

---

### Post by BathroomNinja on 2005-12-20
Thanks as well.  I had this setup back when I was running gentoo on my laptop, but I forgot how I had fixed the issue after I installed Ubuntu.  I was just dealing with it.  Now, I don't have to!

---

