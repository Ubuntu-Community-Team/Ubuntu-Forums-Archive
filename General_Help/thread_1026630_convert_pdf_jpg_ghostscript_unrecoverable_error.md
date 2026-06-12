---
title: "convert pdf jpg ghostscript unrecoverable error"
date: 2008-12-31
forum: General Help
---

### Post by linuxvacuum on 2008-12-31
I cannot convert pdf files to jpg anymore in ubuntu 8.10 because after I type this:```
convert a.pdf b.jpg
```
I get this:
```
Error: /typecheck in --run--
Operand stack:
   --nostringval--   --dict:8/8(L)--   1   --dict:8/8(L)--   1   Rect
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1905   1   3   %oparray_pop   1904   1   3   %oparray_pop   1888   1   3   %oparray_pop   --nostringval--   --nostringval--   2   1   10   --nostringval--   %for_pos_int_continue   --nostringval--   --nostringval--   --nostringval--   --nostringval--   %array_continue   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--
Dictionary stack:
   --dict:1157/1684(ro)(G)--   --dict:1/20(G)--   --dict:75/200(L)--   --dict:75/200(L)--   --dict:106/127(ro)(G)--   --dict:275/300(ro)(G)--   --dict:22/25(L)--   --dict:4/6(L)--   --dict:22/40(L)--   --dict:20/23(L)--
Current allocation mode is local
Last OS error: 2
**GPL Ghostscript 8.63: Unrecoverable error, exit code 1**
convert: Postscript delegate failed `a.pdf': No such file or directory.
convert: missing an image filename `b.jpg'.

```

---

### Post by linuxvacuum on 2009-01-01
*bump*

---

### Post by linuxvacuum on 2009-01-02
I can read the same pdf fine with GIMP.

---

### Post by kaibob on 2009-01-03
Do you get that error message when using convert with all PDF's from all sources. I ask because Ghostscript--which convert uses to read PDF files--is unable to read some files that can be read by Gimp and other programs. You can try to open the file directly with Ghostscript (gs filename) and you may want to check the file with pdfinfo (pdfinfo filename). But, there's no fix that I know of other than to upgrade to a later version of Ghostscript.

---

### Post by linuxvacuum on 2009-01-03
I found out what caused the crash. I had the density option set to 300 and by lowering it to 150 it doesn't crash anymore.

Look this article up for interesting options, especially leading zeros in generated filenames :
 [**ImageMagick: A graphics wizard for the command line**]("http://www.linux.com/articles/113978")

---

### Post by kaibob on 2009-01-03
> **linuxvacuum said:**
> I found out what caused the crash. I had the density option set to 300 and by lowering it to 150 it doesn't crash anymore.

Look this article up for interesting options, especially leading zeros in generated filenames :
 [**ImageMagick: A graphics wizard for the command line**]("http://www.linux.com/articles/113978")

That's weird--I wonder why a density of 300 would cause it to crash and why the command, convert a.pdf b.jpg, would crash.

---

### Post by linuxvacuum on 2009-04-04
I believe it crashes depending if the pdf has a large number of pages. It is probably a ghostscript problem to manage its memory. When the conversion is occuring, my system doesn't respond even if I give it the lowest priority with nice and ionice, gs takes up 100 % cpu AND hard drive i/o ressources!

---

### Post by Cyril_J on 2011-05-21
If the goal is to use Ghostscript at all cost, I have no solution.

If the goal is to have your PDF converted to JPG whatever the solution, you can also use a [PDF to JPG online converter]("http://pdf2jpg.net/"). Just upload your PDF and download the resulting JPG.

If an error occurs during the processing of your document, that will be on the server, not on your PC :P

---

### Post by Zandy on 2011-11-28
I got the simlar error:

... ...
mypc:/Zandy$ convert -density 300x300 a.pdf a.png
... ...
Current allocation mode is local
Last OS error: 28
GPL Ghostscript 8.54: Unrecoverable error, exit code 1
convert: unable to read image data `/tmp/magick-XXaLMjmo'.

I resolved the issure just like this:
mypc:/Zandy$ sudo convert -density 300x300 a.pdf a.png


.... maybe the account does not have related permission.

---

### Post by jobjol on 2012-02-13
I can't help you with ghostscript errors, but maybe [pdfjpg.net]("http://pdfjpg.net") is worth a try. The suggestion of cyril_j is good but that site limits you in PDF size and it is slow.

---

