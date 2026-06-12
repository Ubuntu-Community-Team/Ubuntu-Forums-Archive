---
title: "How to disable timer on duel boot?"
date: 2009-07-30
forum: Desktop Environments
---

### Post by NoonienSoong97 on 2009-07-30
Hi,

I am wondering how I can either disable the timer on the duel boot screen, or change the time to a longer period say like 500 sec. instead of 10 sec.?

Thanks

---

### Post by ibutho on 2009-07-30
Edit /boot/grub/menu.lst and change the "timeout" value from 10 to whatever you want.

---

### Post by NoonienSoong97 on 2009-07-30
I am able to open the file in a text editor, but I am denied to making changes to the file. Or am I only allowed to change it in an admin setting? However the admin password window doesn't popup when I try to resave it.

---

### Post by ibutho on 2009-07-31
You need to be in the admin group, then run something like Alt-F2 and enter "gksudo /boot/grub/menu.lst". Alternatively go to Applications -> Accessories -> Terminal and enter
```
sudo nano /boot/grub/menu.lst
```

---

