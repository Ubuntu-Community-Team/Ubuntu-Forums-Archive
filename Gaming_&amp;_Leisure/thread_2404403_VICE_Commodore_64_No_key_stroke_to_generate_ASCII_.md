---
title: "VICE Commodore 64 No key stroke to generate ASCII graphic on @ key"
date: 2018-10-23
forum: Gaming &amp; Leisure
---

### Post by Ralph Hinkley on 2018-10-23
Computer: Thinkpad x230 convertible laptop
OS: Ubuntu 16.04
Software: VICE commodore 64 emulator version 2.4.25 (GTK+ AMD64/x86_64 Linux glibc 2.23 GCC-5.3.1)

This may be the dumbest problem anyone has ever posted about-

Recently, for fun and nostalgia, I've been programming in Commodore 64 BASIC. While programming I needed to type the ascii character you get from the combo "SHIFT @". (It's a lower right hand corner looking thing.) The problem- My keyboard doesn't have a dedicated @ key. So I did what any slightly above noob level linux user would do- I researched how to remap my keyboard and made my right control key into an @ key using this terminal command:

```
xmodmap -e "keycode 105 = at"
```

This came SO CLOSE to working! It did give me a dedicated @ Key which works in VICE. I can get the ascii symbol that results from the "C= @" combo, but for whatever reason the "SHIFT @" combo only results in an "@", not the ascii character I'm looking for. GAH!!!

Now, before anyone spends too much brainpower, allow me to say that I have worked around this by writing my program which a substituted character, the using POKE 1024+(column)+(row*40),122 to place the character into my program then go up to the line and hit return. So the immediate problem is solved, but I really wish I knew how to fix this.

I have searched google and this forum, and not found ANYTHING that deals with such a weird and specific problem. Any advice would be welcome. Thanks in advance!

---

### Post by Holger_Gehrke on 2018-10-26
If you've installed vice from the repositories, the documentation should be in '/usr/lib/vice/doc/vice_toc.html'. In chapter 4, section 2 there's an explanation of keymap files and there are several examples in '/usr/lib/vice/C64/*.vkm'.

Holger

---

