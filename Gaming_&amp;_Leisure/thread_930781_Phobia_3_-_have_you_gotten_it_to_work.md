---
title: "Phobia 3 - have you gotten it to work?"
date: 2008-09-26
forum: Gaming &amp; Leisure
---

### Post by Zyphrexi on 2008-09-26
when I run it in the terminal, it just complains:

```
./phobia3: error while loading shared libraries: libvorbisfile.so.0: cannot open shared object file: No such file or directory
```

running ```
locate libvorbisfile
``` spits out that I have it, except it's libvorbisfile.so.3, so I'm thinking version mismatch. So I do a 

```
sudo ln -s /usr/lib/libvorbisfile.so.3 libvorbisfile.so.0
```

still no go... or should have I done a

```
sudo ln -s /usr/lib/libvorbisfile.so.3 /usr/lib/libvorbisfile.so.0
``` instead?

---

### Post by Perfect Storm on 2008-09-26
You using 64-bit? [here](http://gaming.gwos.org/doku.php/guides:64bit:phobia_3)

---

### Post by Zyphrexi on 2008-09-26
no, but thanks AI, I was reading that stuff earlier. gj on it.

EDIT: btw that topic doesn't exist. I think you meant this:

[http://gaming.gwos.org/doku.php/guides:64bit:phobia_3](http://gaming.gwos.org/doku.php/guides:64bit:phobia_3)

oh shoot, i just realized that the forums cut off parts of the url.

---

### Post by Perfect Storm on 2008-09-26
aye, just fixed my linked (me blames forum software).

---

### Post by Perfect Storm on 2008-09-26
sudo ln -s /usr/lib/libvorbisfile.so.3 /usr/lib/libvorbisfile.so.0

is the correct.

sudo ln -s /usr/lib/libvorbisfile.so.3 libvorbisfile.so.0
This one will just add a symblink in your current directory. So id you're not in /usr/lib it won't help you.

---

