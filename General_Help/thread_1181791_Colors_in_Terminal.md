---
title: "Colors in Terminal"
date: 2009-06-08
forum: General Help
---

### Post by paulocr on 2009-06-08
Hello,

I would like to know what the colors in a Ubuntu terminal mean when you are browsing a file system.
For example I know the blue means Directory.

Yet in a directory I am browsing I have some files showing in green and others which I added recently in white.

I attach a screenshot, can someone please explain why these files show in white?

I have not played around with the Terminal defaults and these files are causing some unexpected behavior in my application so I suspect there might be something wrong with them.

Thanks,

Paulo

---

### Post by lloyd_b on 2009-06-08
It's a matter of the "attributes" on a file:

White - regular file
Blue - directory
Green - executable file
Cyan - symbolic link
Yellow - device file

(there are probably some more that I don't know about).  As for your screenshot - somehow those files have the "executable" bit set on them.  Do a "ls -l" and look at the attributes. 

Lloyd B.

---

### Post by paulocr on 2009-06-08
You nailed it, thanks very much.
I guess it would still be very interesting to know the whole symbology of the colors. I googled it but could not find it.

---

### Post by Celauran on 2009-06-08
Something like [this](http://linux.die.net/man/5/dir_colors) may be of interest.

---

