---
title: "UP AND RUNNING!!! (need some more help)"
date: 2007-08-03
forum: Desktop Effects &amp; Customization
---

### Post by borovy3488 on 2007-08-03
Guys, this is awesome.  I'm up and running completely in ubuntu.  Everything is working GREAT, and I'm lovin' it.  However, I was just wondering if you guys could help me get beryl on here.  Previously there was a wiki suggested, but its not there anymore.  Can someone explain how to install it?  My video card is just integrated on the Gateway M520HX laptop.

Thanks again,
Wayne:guitar:

---

### Post by splintercellguy on 2007-08-03
[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104) might be helpful. You should also check the other threads in that particular forum section.

---

### Post by Bachstelze on 2007-08-03
Please paste the output of

```
lspci | grep VGA
```

---

### Post by DSn0wMan on 2007-08-03
You should probably be looking at running compiz-fusion, as beryl has merged with compiz. I would start looking here -> [http://www.opencompositing.org/](http://www.opencompositing.org/)

---

### Post by borovy3488 on 2007-08-03
here ya go!!!

"wayne@Waynes-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)"

---

### Post by Bachstelze on 2007-08-03
Ok, you have an Intel integrated graphics chip so you're most certainly running the i810 driver, which is Compiz-compatible. Just install Compiz and off you go :)

[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)


(Moving this to the Desktop Effects forum, by the way.)

---

