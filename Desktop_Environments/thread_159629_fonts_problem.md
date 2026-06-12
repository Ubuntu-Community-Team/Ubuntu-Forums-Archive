---
title: "fonts problem"
date: 2006-04-13
forum: Desktop Environments
---

### Post by sanandana on 2006-04-13
hello,

I would like to use the fonts vu-arial freely available on [http://www.zencomp.com/greatwisdom/fonts/vu-arial-vp.zip](http://www.zencomp.com/greatwisdom/fonts/vu-arial-vp.zip)

this is an unicode fonts set.

I copied the 4 ttf files into /usr/share/fonts/truetype and update the font cache with sudo fc-cache -f -v

but the fonts do not appear in any font menu nor in nautilus fonts:// though firefox recognize them since the website requiring those fonts are displaying properly.

how to fix that? I would like to use those fonts with OOOwriter...

thanks,

sanandana:-D :-D :-D

---

### Post by Ramses de Norre on 2006-04-13
[http://www.ubuntuforums.org/showthread.php?t=20976]("http://www.ubuntuforums.org/showthread.php?t=20976")
I was able to install Tahoma fonts by this.

---

### Post by sanandana on 2006-04-13
thank you for this interrestin link; but it doesn't concern my problem which is the non-recognization of the font by the system.

---

### Post by sanandana on 2006-04-13
can anyone install the font on his system to check if the problem is a common one?

thanks

---

### Post by sanandana on 2006-04-13
here comes the solution: the fonts set is named "VU Arial" but is identified in font.cache-1 as "Arial, VU". It means that there was a conflict between Arial original font and the new one. So I uninstalled Arial and all is ok now.

---

