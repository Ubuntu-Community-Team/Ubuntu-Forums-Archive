---
title: "Duplicate xserver"
date: 2009-12-20
forum: Desktop Environments
---

### Post by hariks0 on 2009-12-20
When I start my ubuntu pc, just before my login, I receive a message that says "An xserver is already started in display :0. Would you like to try starting xserver in another virtual workspace?". Now If I answer 'No' the message appears again and again. If I say 'Yes' It goes to gnome desktop [under display :1] in virtual desktop 9 [Ctrl+Alt+F9] It was previously available only in [Ctrl+Alt+F7] but now available in both F7 and F9. Now I assume that there are two instances of xserver both in [Ctrl+Alt+F7] and [Ctrl+Alt+F9].

I think by killing one instance of xserver manaually I can disable the message. How do I do this?

Thanks in advance.

---

### Post by wasd591 on 2009-12-20
To close the **xserver** process, goto **Terminal** (Applications > Accessories > Terminal). Now type in: 
*killall xserver*

I will work on making a code for so it will stop two from booting up, but for that I will need some code, that is just a temporary solution.

---

### Post by hariks0 on 2009-12-20
Thank you for the quick reply. But the system reply was :-

```
hari@Indira:~$ killall xserver
xserver: no process found
hari@Indira:~$ 
```

I can still access the duplicate desktop in [Ctrl+Alt+F9].

---

