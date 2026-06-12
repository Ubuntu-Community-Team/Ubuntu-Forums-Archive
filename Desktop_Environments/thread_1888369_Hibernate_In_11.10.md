---
title: "Hibernate In 11.10"
date: 2011-11-29
forum: Desktop Environments
---

### Post by NarbeH on 2011-11-29
Hi

I want to hibernate my laptop in Gnome Shell 3.2 11.10.
I can't see the button in my User Menu. I just can see suspend. 
How can I active hibernate?

Thanks

---

### Post by NarbeH on 2011-11-29
Solved. Just made Swap

---

### Post by dcatalano on 2011-12-03
Could you explain what you did to make hibernate work? Not sure what Swap means. Thanks!

---

### Post by NarbeH on 2011-12-03
Without Swap Space, you can't have Hibernate in ubuntu. 
Swap is a partition that is used for low memory's. If you have 1 GB of memory you have to create a partition in 2 GB of swap. so it's a space to help your memory to not get full. 

after creating the swap space, you should edit e fstab file and add the swap information in it. then you will see the hibernate button in the User Menu.

But never mind to make it if you didn't. Hibernate it's not working in 11.10

---

