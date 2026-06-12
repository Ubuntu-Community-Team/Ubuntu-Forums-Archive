---
title: "How to add vista entry to grub"
date: 2009-02-12
forum: General Help
---

### Post by Ameya Koshti on 2009-02-12
I have 500gb hdd on which vista is installed.
Another 160 gb hdd on which xp is installed.
then I installed ubuntu on 160gb(without the 500gb).

so now if i boot from the 160 gb then in the grub i get both
xp and ubuntu.

but now i want to connect both 500gb(primary) and 160gb.


i have added the following entry to menu.lst

title   Windows Vista
root   (hd0,0)
makeactive
chainloader   +1


but it doesn't work..

can any please help me with this?

---

### Post by JK3mp on 2009-02-12
So 500 gig IS your primary and isn't working? Show the whole menu.lst entry

---

### Post by Ameya Koshti on 2009-02-12
menu.lst is intact.
i have only added the vista entry in it.
and when i make 500gb as primary then it just boots into vista.
without giving me an option of booting into xp or ubuntu.which is obvious. so i made 160gb primary...booted in ubuntu...and add the above entry into menu.lst

---

### Post by caljohnsmith on 2009-02-12
How about trying this entry:
```
title       Windows Vista
rootnoverify     (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Let me know if that works or not.

---

### Post by JK3mp on 2009-02-12
OK..for a sec i thought you meant Windows Vista wouldn't load and others would... i was like :S lol. Try the above suggestion and let us know..

---

### Post by Ameya Koshti on 2009-02-13
ok i'll try this.... :)

---

