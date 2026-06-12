---
title: "Unicode in terminal"
date: 2009-02-23
forum: General Help
---

### Post by igor. on 2009-02-23
Hi,

when I create a file with unicode encoding in gedit it works and displays fine. In the GNOME terminal it works too. When I switch over to the terminal (ctrl+alt+1) it doesn't display all special characters, such as "é".

Any ideas how to solve this?

Thanks!

---

### Post by KeyserSoze93 on 2009-02-23
```
unicode_start
``` might work, thought it only displays some unicode chars.

---

### Post by igor. on 2009-02-23
Wow, that works pretty well. However it makes the font bold. Is there any way of changing this behaviour?

---

### Post by igor. on 2009-02-24
Any ideas?

---

### Post by igor. on 2009-02-26
I'd be glad about a tip regarding this problem.

---

### Post by igor. on 2009-02-27
I found a solution. unicode_start messes with setfont and sets some strange font. It's however possible to set this font as an argument, so what I called was:
```
unicode_start /usr/share/consolefonts/Uni1-Fixed16.psf.gz
```
And it worked.

---

