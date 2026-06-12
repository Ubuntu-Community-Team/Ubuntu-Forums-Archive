---
title: "Expanding OS space."
date: 2009-05-01
forum: General Help
---

### Post by chpage07 on 2009-05-01
I installed Ubuntu a long time ago to test it out, I now use it more than I do Windows. When I installed it I only gave it 10 gigs and I have filled that. I have it installed inside Windows Vista and I have plenty of HD space and a second hard drive. Is there anything I can do to give Ubuntu more space?  

I can't repartition because there is no partition to edit.

---

### Post by Marlonsm on 2009-05-01
If you installed it inside Vista, you used Wubi (Windows based UBuntu Installer), and I don't think there is a way to increase the space given to Ubuntu.

I'd suggest you to back up everything and do a clean and normal install, as it not only would give you more space for Ubuntu, but also would speed things up.

But if you can't/don't want to reinstall, just store some files in Vista. Using Ubuntu with Wubi, you can find Vista's files inside /host.

---

### Post by chpage07 on 2009-05-01
That sounds like a plan, thank you very much. I searched the forums but didn't know what the windows loader was called. Now I do.   \\:D/  What is the best way to back up Ubuntu so that when I reinstall it it's exactly the same?

---

### Post by Brian_the_King on 2009-05-01
I also might have to increase the size of my Ubuntu partition in the future.. is there really no simple partition manager for Linux? [like the equivalent of Partition Magic in Windows]

edit: I  realized that I kind of skimmed over the previous posts and missed the Wubi part of the discussion.. I am still curious whether there is a good partition manager to be found.

---

### Post by Marlonsm on 2009-05-01
If you run the Ubuntu LiveCD, you'll find Gparted in it, which is a fairly easy to use partiton manager.

But you won't even need that. During the install it gives you the option to partition the HD and use Ubuntu is Dual boot.
Just don't forget to use Windows' HD defrag before partitioning, it makes the whole processes better.

About backing up, I'm not sure if saving only your Home dircetory somewhere else will do the trick. Maybe someone else can answer that for you.

---

