---
title: "Compose sequences - how to change them?"
date: 2006-06-07
forum: Desktop Environments
---

### Post by virgee on 2006-06-07
Hello everybody,
I got a question about key sequences used with Compose key to achieve inserting special characters not accessible through keyboard in a common manner.

I wonder how I can find and change definition of sequences. I know that there are folders named after locales in /usr/share/X11/locale/ and that there are Compose files in them. But Ubuntu does not look to use files according to locale set, as some combinations do not work. 

Also I would like to be able to change or add some sequnces better suiting for me and laptop keyboard I use, for example to define that <Multi_key> <a> <a> stands for dollar sign or so.

Thx for help.

Virgee

---

### Post by free-zombie on 2006-06-19
*bump*
I have the same problem. Maybe there is a seperate solution to compose that works just as well... I am interested in this for typing Esperanto (i.e. <Multi_key> <u> <x> for &#365; (U+016D) and analogues for &#285;, &#265;, &#309; and &#349;, none of which can be composed afaik)

---

### Post by donmiguel on 2007-09-05
well, does someone of the specialists know how that could be arranged?
thanks, donmiguel

---

### Post by donmiguel on 2007-09-11
seems to be given in the gtk/gtkcomposekeys.c (or similar) files... well, on should go change the source file in the cvs if he gets that stuff :)

---

