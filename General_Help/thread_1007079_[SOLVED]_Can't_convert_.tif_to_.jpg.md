---
title: "[SOLVED] Can't convert .tif to .jpg"
date: 2008-12-10
forum: General Help
---

### Post by Nazty_Nayt on 2008-12-10
Hey guys I scanned some photos for the first time, and did some research, and apparently if I use mogrify I can convert the tifs to jpg's.  I think I'm doing something wrong though, here's the line I'm running.

```

:~/Desktop/photos$  mogrify -format jpg -quality 90 bday3.tif

```

And this is what I get back...

```

mogrify: bday3.tif: unknown field with tag 512 (0x200) encountered. `TIFFReadDirectory'.
mogrify: bday3.tif: unknown field with tag 513 (0x201) encountered. `TIFFReadDirectory'.
mogrify: bday3.tif: unknown field with tag 514 (0x202) encountered. `TIFFReadDirectory'.
mogrify: bday3.tif: unknown field with tag 37677 (0x932d) encountered. `TIFFReadDirectory'.
mogrify: bday3.tif: unknown field with tag 37678 (0x932e) encountered. `TIFFReadDirectory'.
mogrify: bday3.tif: unknown field with tag 37680 (0x9330) encountered. `TIFFReadDirectory'.
mogrify: Sorry, requested compression method is not configured. `bday3.tif'.

```

Can anyone help me out here?

---

### Post by geirha on 2008-12-10
I'd try convert instead, it's almost the same as mogrify, but convert creates a new file and leaves the original intact, while mogrify replaces the original.

```
convert bday3.tif -quality 90 bday3.jpg
```

Do you get the same messages with that command? also what does identify say?
```
identify bday3.tif
```

---

### Post by Nazty_Nayt on 2008-12-10
Thanks Geirha that works.  Will mark as solved.

:guitar:

---

