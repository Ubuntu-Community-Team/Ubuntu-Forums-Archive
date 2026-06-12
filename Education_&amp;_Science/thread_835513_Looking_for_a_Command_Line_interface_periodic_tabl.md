---
title: "Looking for a Command Line interface periodic table"
date: 2008-06-20
forum: Education &amp; Science
---

### Post by Ioky on 2008-06-20
I was looking for a CLI periodic table for my CLI only laptop. it doesn't have be to super powerful, all I want is general information. 

Also if you know some nice CLI science application, can you please let me know?

Thanks

---

### Post by mali2297 on 2008-06-20
[The Electronic Periodic Table of the Elements]("http://www.toddmiller.com/epte/")

I think **build-essential** and **libncurses5-dev** are the only requirements to compile from source. 

Note: 
There seems to be a bug in the code. In definitions.h, line 519:
```

  {"Hydrogen bonding := The bond hydrogen forms with other atoms with hydrogen\n
forming an ionic type interaction with negatively charged atoms of other\n
compounds."}, 

```

Add [color=red]\[/color] before the line breaks, so that it becomes
```

  {"Hydrogen bonding := The bond hydrogen forms with other atoms with hydrogen\n[color=red]\[/color]
forming an ionic type interaction with negatively charged atoms of other\n[color=red]\[/color]   
compounds."}, 

```

After this fix, the program should compile when you run *make*.

---

### Post by Ioky on 2008-06-20
oh thanks.

---

### Post by linuxgod on 2012-02-09
Hi,

I think I will write one. Something simple. I'll post the link here when it's done.

Cheers,
SB

---

### Post by overdrank on 2012-02-09
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

