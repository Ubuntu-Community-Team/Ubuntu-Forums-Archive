---
title: "Random freezing?"
date: 2009-06-10
forum: General Help
---

### Post by Dj TweeX on 2009-06-10
Hello,
useually after a fresh install of 9.04 my laptop will freeze. no kernal panic, nothing odd going on. it will just freeze. as far as i can tell its not related to a specific program. any information you need i will supply. but i hate having to do a hard shutdown everytime it freezes.
~~Gabe~~

---

### Post by blueridgedog on 2009-06-10
It may be getting hot.  Look at these threads:

[http://ubuntuforums.org/showthread.php?t=1176813](http://ubuntuforums.org/showthread.php?t=1176813)

[http://ubuntuforums.org/showthread.php?t=1129135](http://ubuntuforums.org/showthread.php?t=1129135)

Do you have the sensors package installed so you can check the temp?

---

### Post by Dj TweeX on 2009-06-10
its not overheating.
sometimes it will stay on all night (on a wooden nightstand with circulation) sometimes ill turn it on & it will freeze in three minutes. i know for a fact its not a temp issue.

---

### Post by Dj TweeX on 2009-06-10
heres the specs on the laptop i should have said this first

Hp Mini 1030NR
1.6 Ghz Duel thread Intel Atom
1 Gb ram + 1 Gb swap*
16 Gb SSD (/home)
8 Gb Inset Flash drive (/)(*1 Gb Swap)
Ubuntu 9.04 Fresh install

---

### Post by blueridgedog on 2009-06-10
Can you kill the xwindows server with CTRL+ALT+Backspace when it freezes?

---

### Post by Dj TweeX on 2009-06-10
i havent re-enabled it yet. i will try that and get back to you the next time it freezes. shouldnt be to long haha

---

### Post by Dj TweeX on 2009-06-11
I ended up just upgrading to 9.10. which fixed the problem. but i have come across a different problem which i will make a thread for. anyway the wireless has stopped working. the ystem doest read the interface. any thoughts?

---

### Post by blueridgedog on 2009-06-11
I am not a wireless guru, but there are plenty here.  Those that are likely to help you will want to know the make of your wireless card/device.  You can get that via:

```
lspci
```

---

### Post by blueridgedog on 2009-06-11
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)

---

### Post by Dj TweeX on 2009-06-25
i believe the problem was the ZIF cable connecting my SDD to my motherboard.
after i removed my hard drive & ran ubuntu from my flash drive )installed not live) it works fine. i ordered a new one.
just thought id let all of you know

---

