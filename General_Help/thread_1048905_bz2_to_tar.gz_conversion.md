---
title: "bz2 to tar.gz conversion"
date: 2009-01-23
forum: General Help
---

### Post by krishna1650 on 2009-01-23
hi every one.
i got a icon theme from [http://www.deviantart.com/download/60344910/LiNsta_Icons_by_tiennou44.bz2](http://www.deviantart.com/download/60344910/LiNsta_Icons_by_tiennou44.bz2) ,but this is in bz2 format. theme manager needs tar.gz format. so how to convert it.

---

### Post by Slim Odds on 2009-01-23
> **krishna1650 said:**
> hi every one.
i got a icon theme from [http://www.deviantart.com/download/60344910/LiNsta_Icons_by_tiennou44.bz2](http://www.deviantart.com/download/60344910/LiNsta_Icons_by_tiennou44.bz2) ,but this is in bz2 format. theme manager needs tar.gz format. so how to convert it.

tar is an archive that combines many files into one.

bz2 and gz are compression schemes that compress one file.

So it's hard to tell what you need.

the equivalent of a .tar.gz file is a .tar.bz2 file.
the equivalent of a .bz2 file is a .gz file.

---

### Post by krishna1650 on 2009-01-23
> **Slim Odds said:**
> tar is an archive that combines many files into one.

bz2 and gz are compression schemes that compress one file.

So it's hard to tell what you need.

the equivalent of a .tar.gz file is a .tar.bz2 file.
the equivalent of a .bz2 file is a .gz file.

so how to convert it to tar file ?
thanks for help.

---

### Post by jerome1232 on 2009-01-23
You would use bunzip to decrompess it then gunzip to compress it. After running bunzip2 it will lose it's .bz2 extension and just be named archive.tar, after gziping it will gain a .gz extension.

bzip2 and gzip are just different methods of compression.

```
bunzip2 /path/to/compressed/archive
gzip /path/to/compressed/archive
```

---

### Post by krishna1650 on 2009-01-24
> **jerome1232 said:**
> You would use bunzip to decrompess it then gunzip to compress it. After running bunzip2 it will lose it's .bz2 extension and just be named archive.tar, after gziping it will gain a .gz extension.

bzip2 and gzip are just different methods of compression.

```
bunzip2 /path/to/compressed/archive
gzip /path/to/compressed/archive
```

using bunzip2 & gzip i get .gz file. then using tar i get .tar.gz file. but theme manager could not install it, it says error extracting the theme.

thanks once again.

---

### Post by jerome1232 on 2009-01-24
Then take a look in there, they probably packaged it differently (there's a binary install in there, maybe a readme file that tells you what to do)

---edit--- wait it's not an archive in the first place?? Just a compressed file?

(so it was just file.bz2, not file.tar.bz2)

---

### Post by mssever on 2009-01-24
The theme manager can handle both .tar.gz and .tar.bz2. So if you're getting errors, they're because whoever packaged the theme did it wrong, and you should complain to them.

---

