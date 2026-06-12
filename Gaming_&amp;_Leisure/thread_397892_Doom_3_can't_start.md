---
title: "Doom 3 can't start"
date: 2007-03-31
forum: Gaming &amp; Leisure
---

### Post by izanbardprince on 2007-03-31
> ./doom.x86: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory

How do I fix this?

BTW, I'm on Feisty AMD64.

---

### Post by Monk-e on 2007-03-31
You need to install the package 'libxcb-xlib0'. All in all I'm not sure doom 3 works with an AMD64 kernel.

---

### Post by rajeev1204 on 2007-03-31
Hi

doom 3 works fine on a amd 64 version . Iam on dapper 64 and it runs well .


However the error u seem to have is probably cos u are running the game on feisty ( a beta release :) )

I have seen other users talking about that on the feisty section.

But as monk says , try to install the miising package to see if it solves the problem


regards

rajeev

---

### Post by izanbardprince on 2007-03-31
> **Monk-e said:**
> You need to install the package 'libxcb-xlib0'. All in all I'm not sure doom 3 works with an AMD64 kernel.

It works fine now, it said that package was already installed, but when I started DOOM 3 again it loaded just fine.

Yeah, it works on AMD64, you just need the 32-bit libraries.

---

