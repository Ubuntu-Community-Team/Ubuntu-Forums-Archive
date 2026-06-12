---
title: "How do I mount an iso..."
date: 2009-03-18
forum: General Help
---

### Post by honeybadgerman on 2009-03-18
can someone give me the specific code for mounting an iso if the iso is in a folder (Halo Combat Evolved) on the desktop?

---

### Post by Vince4Amy on 2009-03-18
One quick google search would have got you:

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

---

### Post by fcuk112 on 2009-03-18
```

mkdir /media/isopoint
mount xxx.iso /media/isopoint -t iso9660 -o loop

```

---

### Post by MrWES on 2009-03-18
From the terminal:

sudo mkdir /media/iso
sudo mount -o loop /path/to/iso /media/iso

Or you can install gisomount

sudo apt-get install gisomount

Bill

---

### Post by 2hot6ft2 on 2009-03-18
gmount-iso works for me
You can install it thru synaptic by doing a search for gmount-iso or use this in a terminal
Applications>Accessories>Terminal
```
sudo apt-get install gmount-iso
```

---

### Post by honeybadgerman on 2009-03-18
i went with the gisomount, how do i mount now?

---

### Post by D3ath on 2009-03-18
> **honeybadgerman said:**
> i went with the gisomount, how do i mount now?

Follow this link and this will show you how it is done!

[http://tinyurl.com/chdh7o](http://tinyurl.com/chdh7o)

---

### Post by honeybadgerman on 2009-03-18
haha, alright, thanks.

---

### Post by D3ath on 2009-03-18
> **honeybadgerman said:**
> haha, alright, thanks.

It was perfect time to use lmgtfy.com lol thanks for being cool with it!

---

### Post by honeybadgerman on 2009-03-18
that's all well and good, but that tells me how to use gmountiso, not gisomount. i tried the command line for gmountiso, but it didn't work, "packet not found" i had my hardy disk in when i tried. i also looked in the add/remove section, that was no help.

---

### Post by honeybadgerman on 2009-03-18
hey, np. i can take a joke.

---

### Post by Ampersand. on 2009-05-21
thanks for the gmountISO idea. worked a lot better than gISOmount for mounting a movie.

---

### Post by dmizer on 2009-05-21
> **Ampersand. said:**
> thanks for the gmountISO idea. worked a lot better than gISOmount for mounting a movie.

For movies, VLC media player can play a movie iso without the need for mounting. Just open VLC, select "file" > "open file", browse to the iso, and off you go.

---

