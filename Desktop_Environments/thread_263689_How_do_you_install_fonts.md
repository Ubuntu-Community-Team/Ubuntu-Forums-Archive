---
title: "How do you install fonts?"
date: 2006-09-23
forum: Desktop Environments
---

### Post by hk_2999 on 2006-09-23
Can anyone help me know how I can easily install fonts, and any information that I can use regarding installing different font formats? Exampe psfu, truetype, etc.

---

### Post by fritz_monroe on 2006-09-23
How about [this thread]("http://ubuntuforums.org/showthread.php?t=85139")?  Or there's also this page on [Installing Windows True Type Fonts in Linux]("http://smorgasbord.net/how_to_install_true_type_fonts_ubuntu_linux")

---

### Post by hk_2999 on 2006-09-24
Thanks. :D

---

### Post by Shay Stephens on 2006-09-24
The easy way I do it is create a .fonts folder in my home folder and then copy my fonts to that folder.  Easy.

---

### Post by hk_2999 on 2006-09-24
Whoa! Even better. Thanks&#8322;

---

### Post by NickUhlig on 2007-09-03
This doesn't work for me.  I've done BOTH things (created a .fonts directory under home, AND added the ttf font to my /usr/share/fonts/truetype/myfonts directory) and the font I added still does not appear in any of my programs.

Any reason why this might be happening?  When I run fc-cache -f -v it shows that it cached the font in my myfonts directory, but still nothing happens.

Help!

---

### Post by NickUhlig on 2007-09-03
UPDATE

The font is in my fonts:///, but it is named as "decorative font FINAL", instead of the original name (Organic_Elements.ttf).

Why is this?  It appears under its normal name in ~/.fonts and .usr/share/fonts/truetype/myfonts, but not in fonts:///

What is going on here?

---

### Post by honkey on 2008-07-01
I've created a .fonts directory in home but i can't find it anymore
If i try to create a new one it say directory exists.

---

