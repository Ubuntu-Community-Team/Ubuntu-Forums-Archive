---
title: "Search by file type"
date: 2010-02-25
forum: Desktop Environments
---

### Post by prezbedard on 2010-02-25
Is it at all possible to search for files by "type" in Ubuntu? I am using Ubuntu 8.04LTS for the record. I often search for particular file types that may have different extensions images for example.  There doesn't seem to be any way of tweaking the search tool to do that though.

Thanks!

---

### Post by Kakers on 2010-02-25
In terminal type

locate *.<filetpye>

Example: locate *.jpg
will locate all jpg files.

---

### Post by prezbedard on 2010-02-25
> **Kakers said:**
> In terminal type

locate *.<filetpye>

Example: locate *.jpg
will locate all jpg files.

Yes I know how to search by file extension but what about a general image search so it will search for jpgs, pngs, gifs etc. without having to perform separate searches.

---

### Post by Kakers on 2010-02-25
Like?

> locate *.jpg *.png *.txt *.mp3

---

### Post by kealan on 2010-09-14
Actually, prezbedard has a valid (and still unanswered) question.  Using the suggested method, to find (most of) the image files on a hard drive one could have to type:

locate *.bmp *.gif *.jpg *.png *.psd *.thm *.tif *.yuv *.nef *.2bp &#65279;*&#65279;.abm *.adc *.afx *.agif *.agp *.apng *.art &#65279;*.arw *.awd *&#65279;.blkrt *.bm2 *&#65279;.can *.cd5 *&#65279;.cin *&#65279;.cit *&#65279;.cpt *&#65279;.dib *&#65279;.dt2 *&#65279;.fpx *&#65279;.gbr *&#65279;.gih *&#65279;.gim *&#65279;.hdp *&#65279;.jas *&#65279;.jbr *&#65279;.jng *&#65279;.kodak *&#65279;.msp *&#65279;.orf *&#65279;.odi *&#65279;.pbm &#65279;*.pcd &#65279;*.psp *.psd *&#65279;.raf *&#65279;.wb1 *.yuv

---

### Post by asmoore82 on 2010-09-14
Not the most efficient thing in the world =D ...

```
find *<some_dir>* -type f -exec file '{}' ';' | grep -i image
```

---

