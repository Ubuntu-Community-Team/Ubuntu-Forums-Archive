---
title: "bulk renaming of files"
date: 2009-03-04
forum: General Help
---

### Post by azza777 on 2009-03-04
Hey guys & Gals

I have search the internet high and low found various answers but nothing that can do what im after, so im hoping someone in here can help em out;

I have a heap of mp3 files and want to remove the start track numbers like so:

001 - Metallica-One.mp3
002 - Nikki Webster - Slayer.mp3

to

Metallica-One.mp3
Nikki Webster - Slayer.mp3

so removing the "00X -" part

i know theres someway of bulk doin this in the terminal, Does anyone have the know how and patience to kindly step me through this?

Thanx in advance

---

### Post by lykwydchykyn on 2009-03-04
There are several user-friendly renaming tools in the repositories.  I've used gwenrename, though it's a KDE program and you might not want to have all the KDE dependencies loaded in.  There's even mp3rename, which is specially aimed at renaming mp3's.  Try searching Synaptic for "rename".

---

### Post by kaibob on 2009-03-04
Lots of ways to do this. If the characters to be removed is a set number, use the following in a terminal window:

```
rename -n 's/^.{n}//' *.mp3
```

Change "n" to the number of characters to be removed. The -n option directs rename to do a dry run and report proposed changes; substitute -v for -n to actually change the files.

---

### Post by mb_webguy on 2009-03-05
> **azza777 said:**
> Hey guys & Gals

I have search the internet high and low found various answers but nothing that can do what im after, so im hoping someone in here can help em out;

I have a heap of mp3 files and want to remove the start track numbers like so:

001 - Metallica-One.mp3
002 - Nikki Webster - Slayer.mp3

to

Metallica-One.mp3
Nikki Webster - Slayer.mp3

so removing the "00X -" part

i know theres someway of bulk doin this in the terminal, Does anyone have the know how and patience to kindly step me through this?

Thanx in advance

If you install GPRename, you can either set it to clip the first six spaces off the filename (assuming all of them follow the "000 - " pattern), or you can replace the regular expression "[0-9][0-9][0-9] - " with nothing.

---

### Post by azza777 on 2009-03-05
thanks guys ill have a go at these and let ya know how i went! :popcorn:

---

