---
title: "cannot install vim72 with gui support from source"
date: 2009-03-08
forum: General Help
---

### Post by doctor bangali on 2009-03-08
I cannot install vim72 with gui support from source. 

I run configure as:

./configure --with-features=huge --enable-gui=gnome2 --enable-cscope --enable-pythoninterp
.

Notice this in the output:

checking if X11 header files can be found... no
checking --enable-gui argument... no GUI support
checking X11/SM/SMlib.h usability... yes
checking X11/SM/SMlib.h presence... yes
.

I have the libX11-dev package installed.

Any idea whats happening?

---

