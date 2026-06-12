---
title: "Where can i find the Lucida Typewriter font?"
date: 2005-08-07
forum: Desktop Environments
---

### Post by sk545 on 2005-08-07
Is it in a repository or is it something one has to buy?  All i have so far is Lucida Sans, Lucida Console, and Lucida Sans Unicode.

Thanks.

---

### Post by SFN on 2005-08-07
Try this:

[http://ubuntuguide.org/#extrafonts](http://ubuntuguide.org/#extrafontshttp://)

---

### Post by sk545 on 2005-08-07
i have already installed msttcorefonts and gsfonts-x11.  There is no Lucida Typewriter in there.

---

### Post by SFN on 2005-08-07
I just looked and I do have it but it looks like it came with java.

Take a look in /usr/java/jre1.5.0_02/lib/fonts/.

---

### Post by sk545 on 2005-08-09
wow, thats really weird...how do i add those to the font path for the system?

---

### Post by marekm on 2005-08-10
simply;
#dpkg-reconfigure fontconfig
and choose enable type1 (or bitmap) fonts (or something simillar ;) i think you will know )
 it should help...

best regards 

marekm

---

### Post by yetihehe on 2007-10-28
But where can I find Lucida console? I have Lucida Bright and Typewriter, which came with java. after installing gsfonts there is no -Console either. Ihave installed msttcore too.

---

