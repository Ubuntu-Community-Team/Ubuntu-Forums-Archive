---
title: "Re-organize the list of kernels at startup"
date: 2009-06-02
forum: General Help
---

### Post by rcayea on 2009-06-02
I have two kernels listed at startup. One is the 2.6.28-12 pre-release which I fiddle with. The other is the stable 2.6.28-11 which I use as my day-to-day boot. 

My question is, I want to make the 2.6.28-11 kernel first on my list so that is the one that automatically gets loaded but I want to keep the 2.6.28-12. 

Right now, my comp defaults to the 2.6.28-12 kernel and the thing is, I like to power on my computer and then go get changed out of my work clothes or something and come back to my computer loaded up and ready to go. Any way to make it so 2.6.28-11 is the first kernel listed?


Any thoughts? If you need more info please let me know. 


Thanks,
Randy

---

### Post by rcayea on 2009-06-02
bump

---

### Post by gforster on 2009-06-02
It has been awhile, but I believe you need to edit /boot/grub/menu.lst

I think that Ubuntu Tweak also has an option of making a certain one the default, but it does not reorder them.

---

### Post by rcayea on 2009-06-02
Thanks. I'll look into your suggestion. 

Randy

---

