---
title: "to to fix disk errors"
date: 2009-10-29
forum: Desktop Environments
---

### Post by Mia1990 on 2009-10-29
hello all,

well during a fsck scan it pointed that i have some disk errors and i dont think it fixed it would anyone know of a software that can do this for me i am still using 9.04 i have not upgraded yet as i would like to fix these first.

Thank you

---

### Post by m4tic on 2009-10-29
why didnt you jst used it? it works
But it once failed and messed up my systme two weeks back after i did a partition resize

code: sudo fsck -f -y -v

---

### Post by twright on 2009-10-29
> **Mia1990 said:**
> hello all,

well during a fsck scan it pointed that i have some disk errors and i dont think it fixed it would anyone know of a software that can do this for me i am still using 9.04 i have not upgraded yet as i would like to fix these first.

Thank you
If you run fsck when logged in a root (go into recovery console at boot) this should fix the errors.

However a much better idea would be to do a fresh install of Karmic; this would fix any errors and allow you the use the new, better ext4 filesytem as well.

---

### Post by Mia1990 on 2009-10-29
I think i am going to do a  fresh install of Karmic.I have a lot of stuff to back up and was thinking i could just do a upgrade.So if i upgrade i can't use the new ext4 filesystem?
Thanks

---

### Post by twright on 2009-10-30
> **Mia1990 said:**
> I think i am going to do a  fresh install of Karmic.I have a lot of stuff to back up and was thinking i could just do a upgrade.So if i upgrade i can't use the new ext4 filesystem?
Thanks
Yes, not easily at least. In any case this would still leave you with any disk errors intact.

---

### Post by khelben1979 on 2009-11-09
I think that [Spinrite]("http://en.wikipedia.org/wiki/Spinrite") would be able to solve your problem, unfortunately it's not free software.

[SpinRite on YouTube]("http://www.youtube.com/watch?v=4x_KlRlcqNI").

---

### Post by CAPLinux on 2009-11-09
> **khelben1979 said:**
> I think that [Spinrite]("http://en.wikipedia.org/wiki/Spinrite") would be able to solve your problem, unfortunately it's not free software.

[SpinRite on YouTube]("http://www.youtube.com/watch?v=4x_KlRlcqNI").

Oh man you stole my thunder.  Spinrite isn't free, but it is the best drive maintenance and recovery tool out there.  It is well worth the $89

---

### Post by Mia1990 on 2009-11-10
Thank you all spinrite came up on my search but because i know how most of the world thinks that windows is all there is i did not know how it would work with a linux based computer.Any other idea's?Thank you

---

### Post by khelben1979 on 2009-11-11
> **Mia1990 said:**
> Thank you all spinrite came up on my search but because i know how most of the world thinks that windows is all there is i did not know how it would work with a linux based computer.Any other idea's?Thank you

SpinRite can fix your EXT3 partition. It does not only fix Windows partitions.

---

