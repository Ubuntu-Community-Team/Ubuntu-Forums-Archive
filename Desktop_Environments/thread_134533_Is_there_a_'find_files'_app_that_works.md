---
title: "Is there a 'find files' app that works?"
date: 2006-02-22
forum: Desktop Environments
---

### Post by solusrex on 2006-02-22
Hello,

I have never ever had any luck with kfind. Not once has it ever found a file for me in any version of linux I've used. Am I being really stupid? For instance, I have 6 different versions of a song called 'fate in a pleasant mood'. If I search for any of those words no files are found no matter how I fiddle with the options.

On the cli slocate works, but I would really like a gui for searching. Is there an slocate gui? What does kfind use if not slocate?

Are any of these beagle-type-apps ready for the kubuntu desktop?

---

### Post by welsh_spud on 2006-02-22
I THINK there is a program for KDE called Kat. I believe it works like beagle somewhat.

[http://kat.mandriva.com/](http://kat.mandriva.com/)

---

### Post by Jucato on 2006-02-22
you could also try to do this in Konqueror:
type "locatel:/*filename_or_search_pattern*" minus the quotation marks.

---

### Post by solusrex on 2006-02-23
Thanks for your responses. The 'locate' tip is great. How come I never heard of it?!?!
 
Kat definitely looks like something to bear in mind. Thanks again.

---

### Post by Jucato on 2006-02-23
[QUOTE=solusrex]Thanks for your responses. The 'locate' tip is great. How come I never heard of it?!?!
 
Kat definitely looks like something to bear in mind. Thanks again.[/QUOTE]

Kinda off topic:

Unfortunately, KDE has so many unpublicized features that are quite awesome. Some of this include:
- Firefox-like search in Konqueror (at the bottom of window) by pressing "/" (ctrl-backspace to delete letters)
- almost all KDE applications can access what KDE calls kioslaves (Kde Input Output slaves) of which "locate:/" is one. In Konqueror, you can have easy access to places like trash:/ (your trash bin), media:/, system:/, home:/, settings:/. Guess what, http:/ and ftp:/ are also kioslaves!
- to demonstrate a power of these kioslaves, try opening a webpage using Kate. Yeah, Kate! Open up Kate, File > Open, and in the Location part, enter a web page (don't forget to put [http://)](http://)) and viola! instant HTML code. :D

---

