---
title: "xorg freezes for no reason"
date: 2009-01-25
forum: General Help
---

### Post by yusuo85 on 2009-01-25
i use intrepid and i keep on having the same problem, my pc freezes up for no reason and while im doing nothing particular.
The mouse works in this state but i cant press any buttons, as does any media thats playing (audio, no moving pictures)
any ideas why this happening and how i can solve it.
Im getting fed up with ubuntu now this version is really buggy in comparison to other releases. Whats the best deb o/s?

---

### Post by yusuo85 on 2009-01-25
i use intrepid and i keep on having the same problem, my pc freezes up for no reason and while im doing nothing particular.
The mouse works in this state but i cant press any buttons, as does any media thats playing (audio, no moving pictures)
any ideas why this happening and how i can solve it.

---

### Post by Dr Small on 2009-01-25
> **yusuo85 said:**
> Whats the best deb o/s?

Debian.

---

### Post by overdrank on 2009-01-25
> **yusuo85 said:**
> i use intrepid and i keep on having the same problem, my pc freezes up for no reason and while im doing nothing particular.
The mouse works in this state but i cant press any buttons, as does any media thats playing (audio, no moving pictures)
any ideas why this happening and how i can solve it.

Hi and if you could give us some system specs this may help. Also 32 bit or 64bit.

---

### Post by yusuo85 on 2009-01-25
its a 3.2ghz with 1.2gb ram ati 128mb firegv graphics card

---

### Post by fixitdude on 2009-01-25
Any chance it might be the screen saver? Try turning it off, changing it etc..
Run the memory test that comes on the boot CD (or get something that has memtest86 on it).

---

### Post by Crafty Kisses on 2009-01-25
Debian would be the answer to one of your questions, but let's try and get down to the root of the problem. Let's see your X logs and let's see if we can see anything in there out of the ordinary:
```
/var/log/Xorg.0.log
```

---

### Post by overdrank on 2009-01-25
Threads merged :)

---

### Post by Kain000 on 2009-01-25
This isnt a result of changing the screen brightness on a laptop is it?  that is a known bug with dell laptops,  but I believe it to be pached.

Or-  A bug I am currently chasing has something do do with bluetooth in my laptop that causes it to freeze up.

---

