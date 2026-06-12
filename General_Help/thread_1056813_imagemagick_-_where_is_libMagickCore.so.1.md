---
title: "imagemagick - where is libMagickCore.so.1 ?"
date: 2009-02-01
forum: General Help
---

### Post by ccaaee on 2009-02-01
Hi All

I've just installed Ubuntu 8.10 and after adding imagemagick I can't seem to get it to work...  Any call to display results in:

display: error while loading shared libraries: libMagickCore.so.1: cannot open shared object file: No such file or directory

I've looked hi and low but can't find the package to add this missing lib.

---

### Post by kaibob on 2009-02-02
I did a google search of the error message, and for most people the issue appears not to be a missing library but a missing path statement. Did you install Imagemagick with synaptic?

---

### Post by joanmunoz on 2009-02-03
I've the same problem. Just installed ImageMagick by command line. I'd to install a PERL library before because I'd a previous error "/usr/bin/ld: cannot find -lperl".

Any help? 

Thx!!

---

### Post by joanmunoz on 2009-02-03
Hi! I've just solved my problem. Through Synaptic, I've installed the rest of ImageMagick libraries (PerlMagick and several libgraphicsmagick listed) and now seems to work right.

Hope this helps!

Regards

Joan

---

