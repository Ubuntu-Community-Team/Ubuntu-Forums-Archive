---
title: "Debian Questions"
date: 2008-06-12
forum: Debian
---

### Post by kevin11951 on 2008-06-12
i wana try Debian in a virtual box, so... my question is, if i have an active internet connection, do i need anything besides the first CD to install the core os?

---

### Post by Playa1313 on 2008-06-12
No, the first install cd is all you need.


Quote from [http://www.debian.org/CD/http-ftp/](http://www.debian.org/CD/http-ftp/)
> The first CD/DVD disk contains all the files necessary to install a standard Debian system.
To avoid needless downloads, please do not download other CD or DVD image files unless you know that you need packages on them.

---

### Post by p_quarles on 2008-06-12
Moved to the Debian section of Other OS Talk.

You don't even need the full CD. The business card or net install disks are all you need.

---

### Post by Arthur Archnix on 2008-06-12
Grab the Net Install iso of Testing, aka Lenny. The second beta of the installer was just released the other day.

[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

---

### Post by markharding557 on 2008-06-12
works fine on virtualbox but it won't tell you how it will work on your real hardware though

---

### Post by kellemes on 2008-06-13
> **markharding557 said:**
> works fine on virtualbox but it won't tell you how it will work on your real hardware though

Debian always works ;-)
Just don't expect the next-next-finish experience of Ubuntu.

---

### Post by markharding557 on 2008-06-13
> **kellemes said:**
> Debian always works ;-)
Just don't expect the next-next-finish experience of Ubuntu.

you are right debian always works but kevin11951 will need to put it on real hardware to be able to compare it to ubuntu and see how much quicker it is

---

### Post by kerry_s on 2008-06-13
for virtual box you might as well just grab the xfce4 version.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

---

### Post by Inxsible on 2008-06-16
One thing to note: 

I used the business iso for testing (Lenny) and the kernel 2.6.24-1 just did not load the sound modules....no matter what I tried.

So I had to downgrade the kernel to 2.6.22-3. If they released a newer kernel, then that might work.

you may wanna check that out.

---

