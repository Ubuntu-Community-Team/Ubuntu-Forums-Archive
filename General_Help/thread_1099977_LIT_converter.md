---
title: "LIT converter"
date: 2009-03-18
forum: General Help
---

### Post by sandyd on 2009-03-18
Can anyone point me towards a Microsoft .LIT converter?

Thanks!

[http://www.kyz.uklinux.net/convlit.php](http://www.kyz.uklinux.net/convlit.php)

doesn't work btw

---

### Post by lloyd_b on 2009-03-18
```
sudo apt-get install convlit
```(or install the "convlit" package via the package manager of your choice.

Then "man clit" (no snarky comments please - that's the name of the command) for info on how to use it.

Lloyd B.

---

### Post by mb_webguy on 2009-03-18
You can use the command "whereis clit" if you can't find it.

(That wasn't too snarky, was it? ;) )

---

### Post by charlesall on 2009-12-08
great app [http://calibre-ebook.com/download_linux](http://calibre-ebook.com/download_linux)

---

### Post by life-on-mars on 2010-01-17
I agree calibre seems to be the best solution for linux.

Use ```
sudo apt-get install calibre
``` to install it.

Alternatively, you could install epub-utils and then do...
```
lit2epub input.lit
``` 

The resulting epub file can be opened with fbreader.

---

