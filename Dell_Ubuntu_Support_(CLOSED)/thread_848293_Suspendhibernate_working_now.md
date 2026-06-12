---
title: "Suspend/hibernate working now"
date: 2008-07-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by N2PTF on 2008-07-03
Both working now on my 530N after most recent nvidia update:)

---

### Post by aidave on 2008-07-03
What nvidia update are you referring to?

Does it work repeatedly (10x in a row), or just once in a while?

---

### Post by aidave on 2008-07-03
I've moved to NVIDIA 173.14.09 from .05, and the latest Ubuntu linux kernel as well.  

Resume has started to work better.  So far no crashes. after 5 resumes.  Will wait and see... I've had my hopes dashed repeatedly with this issue for quite a while now!  :(

---

### Post by N2PTF on 2008-07-03
Sorry I'm still new to Ubuntu. It was a latest update through the download notification icon. A bunch of programs had to do with the Nvidia driver, but I didn't pay too close attention. So far I have been able to suspend/hibernate about 6 times in a row w/o problem

---

### Post by aidave on 2008-07-03
Ok.  I stopped using the Ubuntu NVIDIA updates a long time ago, because the updating was so rare.  You can download the latest NVIDIA Linux drivers from their website.  But if it's workin for you, don't bother! :)

I wonder what driver they have packaged in there, but I dont know how to check.  Anyone know how to read up on package details?

---

### Post by wyth on 2008-08-08
Don't know if this thread is still being read, but I'd love to know how you got this working.

I have a 530n desktop running 8.04 with an Nvidia 8600 GT gfx card with the 173.14.12 driver.  Hibernate works, but coming out of suspend always drops be to a black screen with a cursor.  

This is happening on the 2.6.24-20-generic kernel; I'm going to try rolling back to 2.6.24-19-generic, as on y Lenovo laptop, the 2.6.24-20-generic kernel killed both suspend and automatic network configuration.

---

### Post by PinkFloyd102489 on 2008-08-08
Works just fine on my Inspiron 1720. Using latest Nvidia x86_64 driver and latest Ubuntu kernel. I'll see what happens when I upgrade to the smp kernel for my dual cores.

---

### Post by wyth on 2008-08-10
Hmm... maybe I should finally just try out the 64 bits, but I don't have time to re-install right now.  I tried to get suspend working yesterday, tried the latest Nvidia drivers, and just hosed my entire xorg -- couldn't get anything except vesa 800x600 for most of the day, no suspend, and it left an acrid taste in my mouth.

---

