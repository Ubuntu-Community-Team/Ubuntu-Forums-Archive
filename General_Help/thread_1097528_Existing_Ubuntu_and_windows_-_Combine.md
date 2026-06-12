---
title: "Existing Ubuntu and windows - Combine"
date: 2009-03-16
forum: General Help
---

### Post by studo77 on 2009-03-16
Hi

I have two pc's running. The one was for my schoolwork, just graduated.

The school-pc was running Windows as i needed it for special programs. Now it is needed as a work-pc, for when i want to work at home.

The other is Ubuntu, which i used for gaming and movies.

Now i want to use the graphics from Ubuntu-pc and HW from work-pc. For Ubuntu - no problem, just change the HD. 

And i could use the same for Windows. But i would like to have a dual-boot.

How do i do this when i want to use the two existing installations of OS's?

---

### Post by kuja on 2009-03-16
Well,after you add the hard drive, you'll just need to tell it where Windows is. You'll do this by editing the /boot/grub/menu.lst file. The lines you will add will look something like >  title         Windows 95/98/NT/2000
 root          (hd0,0)
 makeactive
 chainloader   +1
You will have to change the (hd0,0) part to match if it's not the first partition on the first disk as (hd0,0) implies.

Also, Depending on how picky Windows wants to be you might also have to fake Windows into thinking it's on the first disk if it isn't. > map (hd0) (hd1)
map (hd1) (hd0)

This should really be all you need to do to set up convenient dual booting-ness.

---

### Post by studo77 on 2009-03-16
Very nice. I will try it.

And that is damn simple too...

Now i need to see how and where to fit the hd's under my table. Do not want the bulky/ugly case standing around.

---

