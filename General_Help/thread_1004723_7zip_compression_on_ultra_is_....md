---
title: "7zip compression on ultra is ..."
date: 2008-12-07
forum: General Help
---

### Post by eulallia1 on 2008-12-07
I used a command to compress an ISO of mine

```

7z a -mx=9 ./my.iso.7z ./my.iso

```

my.iso is ~2.4 GB (2614231040 bytes) large,
using ratios (because the compression has not finished, ~55%) the 7zip archive should end at 2.3708 GB (2545709688.9 bytes).

I've also compressed an .exe before, it was 234 mb, the compressed was 237,
the question is, why does 7zip compress extremely well on some formats, but not at all on others?

[edit]

Also, should I tarball it first to see if that helps?

---

### Post by jmoorse on 2008-12-07
It is my understanding that certain data types are much more compressible than others.  For example give a shot compressing WAV and MP3 files to illustrate the difference.  Another good example would be BMP and JPG.  Data that already exists in a compressed form will not yield too positive a result when re-compressing.

Of course ratios are ultimately dependent on the compression algorithm...

--Jeff Moorse

---

### Post by eulallia1 on 2008-12-07
> **jmoorse said:**
> It is my understanding that certain data types are much more compressible than others.  For example give a shot compressing WAV and MP3 files to illustrate the difference.  Another good example would be BMP and JPG.  Data that already exists in a compressed form will not yield too positive a result when re-compressing.

Of course ratios are ultimately dependent on the compression algorithm...

--Jeff Moorse

7z has multiple compression algorithms, excluding the compression level?

ISOs aren't compressed  by default (yet can be), I *still* can't figure out what's up with it.

I'll try tarring it maybe? :P

[edit]
Also, compression ended and the archive is 2447256594 bytes (~2.3 GB).

---

### Post by jmoorse on 2008-12-07
I was thinking perhaps the data within the ISO: video files, mp3s, a ISO full of zip files (ok kidding on that last one)

---

