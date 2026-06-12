---
title: "having trouble with .ps files"
date: 2005-05-13
forum: Desktop Environments
---

### Post by newbuntu101 on 2005-05-13
hello everybody,
is there a how-to somewhere that describes how to install ghostscript/postscript ?  i'm using kde and kynaptic to find out which packages to install but nothing seems to come up with the search.  even though i have kghostview, i want to convert from pdf to ps and when i type pdf2ps i'm having errors such as:

Dictionary stack:
   --dict:1119/1686(ro)(G)--   --dict:0/20(G)--   --dict:75/200(L)--   --dict:75/200(L)--   --dict:105/127(ro)(G)--   --dict:251/347(ro)(G)--   --dict:21/24(L)--   --dict:4/6(L)--   --dict:25/32(L)--   --dict:17/17(ro)(G)--   --dict:1119/1686(ro)(G)--
Current allocation mode is local
Last OS error: 2
AFPL Ghostscript 8.51: Unrecoverable error, exit code 1

any ideas?
thanks

---

### Post by ludi on 2005-05-14
There are many apps that can handle .ps stuff. You must enable your universe, multiverse and the unstable debian repositories to get it.
Whatever, you can try open your pdf in any pdf reader (Acrobat Reader 7 preferentially) and print it to file (will save a .ps file).
I think that is better you use the source file and use the Rip's interpretor to convert to ps (then you will match exactly with you print model).
This will depend of what kind of job you are doing.
For professional purpose this is the best way (if they required a "closed" file, you must have to know what kind of print they have and ask for the print profile at least).
Regards

---

### Post by Alexander Kirillov on 2005-05-14
[QUOTE=newbuntu101]hello everybody,
is there a how-to somewhere that describes how to install ghostscript/postscript ? 
[/QUOTE]
gs -- the postscript interpreter -- is installed by default. You are certain to have it already on your system
 
>  i want to convert from pdf to ps and when i type pdf2ps i'm having errors such as:

Dictionary stack:
   --dict:1119/1686(ro)(G)--   --dict:0/20(G)--   --dict:75/200(L)--   --dict:75/200(L)--   --dict:105/127(ro)(G)--   --dict:251/347(ro)(G)--   --dict:21/24(L)--   --dict:4/6(L)--   --dict:25/32(L)--   --dict:17/17(ro)(G)--   --dict:1119/1686(ro)(G)--
Current allocation mode is local
Last OS error: 2
AFPL Ghostscript 8.51: Unrecoverable error, exit code 1

any ideas?
thanks

This happens. pdf2ps can handle most but not all PDF files - 
PDF is complex format. My suggestion would be to install Acrobat Reader and use "print to file". This will oroduce a ps file.

---

