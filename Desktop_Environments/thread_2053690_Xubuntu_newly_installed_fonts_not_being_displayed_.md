---
title: "Xubuntu newly installed fonts not being displayed correctly"
date: 2012-09-05
forum: Desktop Environments
---

### Post by khalidaziz on 2012-09-05
Hi,

I recently installed a bunch of fonts by cp'ing them over to /usr/share/fonts

Unfortunately, my newly installed fonts are all being rendered as a bunch of boxes, without letters. I'm a migrant from Gnome 2, where installing fonts worked out of the box. My Xubuntu version is 12.04. Does anybody have an idea of what's going on? See below for what they're being rendered as:

[IMG]http://img821.imageshack.us/img821/3534/screenshot0905201210353.png[/IMG]

---

### Post by vasa1 on 2012-09-05
> **khalidaziz said:**
> Hi,

I recently installed a bunch of fonts by cp'ing them over to /usr/share/fonts...
Why don't you try actually installing them the regular way? Maybe some thing is missed out when you cp them over?

---

### Post by khalidaziz on 2012-09-05
I downloaded font manager and tried that - same problem showed up. That screenshot up there is font manager.

---

### Post by Toz on 2012-09-05
Interestingly, I just downloaded the ACME Secret Agent font, sudo copied the 3 files over to /usr/share/fonts and it worked automatically. Also using Xubuntu 12.04.

Have you tried running:
```
sudo fc-cache -vf
```

---

### Post by khalidaziz on 2012-09-06
> **Toz said:**
> Interestingly, I just downloaded the ACME Secret Agent font, sudo copied the 3 files over to /usr/share/fonts and it worked automatically. Also using Xubuntu 12.04.

Have you tried running:
```
sudo fc-cache -vf
```

I'd run it without the verbose tag earlier, but here's the output.

I actually don't see the ACME font in the output, could that be the issue?

Thanks for your help :)


```
khalid@khalid-laptop:/usr/share/fonts$ sudo fc-cache -vf
[sudo] password for khalid: 
/usr/share/fonts: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/cmap/adobe-japan1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/gs-cjk-resource: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 360 fonts, 20 dirs
/usr/share/fonts/truetype/droid: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/fonts-nafees: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 13 fonts, 0 dirs
/usr/share/fonts/truetype/kacst: caching, new cache contents: 15 fonts, 0 dirs
/usr/share/fonts/truetype/kacst-one: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/liberation: caching, new cache contents: 16 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/nanum: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/scheherazade: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/takao-gothic: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/tlwg: caching, new cache contents: 54 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-khmeros-core: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lyx: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu-font-family: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/khalid/.fonts: caching, new cache contents: 0 fonts, 1 dirs
/home/khalid/.fonts/Library: caching, new cache contents: 0 fonts, 23 dirs
/home/khalid/.fonts/Library/A: caching, new cache contents: 37 fonts, 0 dirs
/home/khalid/.fonts/Library/B: caching, new cache contents: 15 fonts, 0 dirs
/home/khalid/.fonts/Library/C: caching, new cache contents: 23 fonts, 0 dirs
/home/khalid/.fonts/Library/D: caching, new cache contents: 22 fonts, 0 dirs
/home/khalid/.fonts/Library/E: caching, new cache contents: 10 fonts, 0 dirs
/home/khalid/.fonts/Library/F: caching, new cache contents: 12 fonts, 0 dirs
/home/khalid/.fonts/Library/G: caching, new cache contents: 36 fonts, 0 dirs
/home/khalid/.fonts/Library/H: caching, new cache contents: 11 fonts, 0 dirs
/home/khalid/.fonts/Library/I: caching, new cache contents: 1 fonts, 0 dirs
/home/khalid/.fonts/Library/J: caching, new cache contents: 26 fonts, 0 dirs
/home/khalid/.fonts/Library/K: caching, new cache contents: 20 fonts, 0 dirs
/home/khalid/.fonts/Library/L: caching, new cache contents: 9 fonts, 0 dirs
/home/khalid/.fonts/Library/M: caching, new cache contents: 18 fonts, 0 dirs
/home/khalid/.fonts/Library/N: caching, new cache contents: 13 fonts, 0 dirs
/home/khalid/.fonts/Library/O: caching, new cache contents: 7 fonts, 0 dirs
/home/khalid/.fonts/Library/P: caching, new cache contents: 13 fonts, 0 dirs
/home/khalid/.fonts/Library/Q: caching, new cache contents: 1 fonts, 0 dirs
/home/khalid/.fonts/Library/R: caching, new cache contents: 8 fonts, 0 dirs
/home/khalid/.fonts/Library/S: caching, new cache contents: 56 fonts, 0 dirs
/home/khalid/.fonts/Library/T: caching, new cache contents: 19 fonts, 0 dirs
/home/khalid/.fonts/Library/U: caching, new cache contents: 7 fonts, 0 dirs
/home/khalid/.fonts/Library/W: caching, new cache contents: 6 fonts, 0 dirs
/home/khalid/.fonts/Library/Y: caching, new cache contents: 7 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
/home/khalid/.fontconfig: cleaning cache directory
fc-cache: succeeded

```

---

### Post by Toz on 2012-09-06
> I actually don't see the ACME font in the output, could that be the issue?
I get:
> /usr/share/fonts: caching, new cache contents: 3 fonts, 5 dirs

What does the following say:
```
ls -l /usr/share/fonts
```

---

### Post by khalidaziz on 2012-09-06
Here you go:

```
khalid@khalid-laptop:/usr/share/fonts$ ls -l /usr/share/fonts
total 28
drwxr-xr-x  4 root root  4096 Aug 17 19:01 cmap
drwxr-xr-x 22 root root 16384 Sep  5 21:38 truetype
drwxr-xr-x  3 root root  4096 Aug 17 19:01 type1
drwxr-xr-x  6 root root  4096 Aug 17 19:02 X11

```

---

### Post by khalidaziz on 2012-09-07
Okay, I rm'd the files from the fonts dir and it suddenly started working. I'm guessing it was a conflict between whatever the font manager did and my own failed cp. Lesson learned: don't randomly mess with system files and hope things work!

Thanks for your help. :)

---

