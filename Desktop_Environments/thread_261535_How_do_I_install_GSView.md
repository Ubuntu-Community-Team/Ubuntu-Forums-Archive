---
title: "How do I install GSView?"
date: 2006-09-20
forum: Desktop Environments
---

### Post by d3dtn01 on 2006-09-20
Yesterday I installed Ghostscript. Now I'd like to install GSView. I downloaded the gunzipped tar file from [www.cs.wisc.edu/~ghost/gsview/](www.cs.wisc.edu/~ghost/gsview/) and then extracted the files. From here, I don't know what to do. There doesn't appear to be anything to compile. Can anyone help?

---

### Post by bswilson on 2006-09-20
> **d3dtn01 said:**
> Yesterday I installed Ghostscript. Now I'd like to install GSView. I downloaded the gunzipped tar file from [www.cs.wisc.edu/~ghost/gsview/](www.cs.wisc.edu/~ghost/gsview/) and then extracted the files. From here, I don't know what to do. There doesn't appear to be anything to compile. Can anyone help?

There are a couple of C files in the folder you extracted.  I noted that there are several folders, corresponding to languages.  You should be able to go into the directory for your preferred language, and then do a make / make install.

---

### Post by d3dtn01 on 2006-09-20
Thanks for the tip, but I was unsuccessful. After changing the directory to 'en', I tried the 'make' command. Nothing happened. The 'en' directory has the following files.

gsview.hpj  gvclang.rc   gvplang.rc  gvxlang.c
gvclang.h   gvclang.txt  gvwlang.rc

---

### Post by bswilson on 2006-09-21
Sorry that I'm not much help.  I am not much of a programmer, so I'm stuck too.  I'll bet someone much smarter than me will follow up to your post.  Good luck!

---

### Post by andrei_m on 2008-06-10
I did install gsview on Ubuntu:

I downloaded package called:
gsview-4.8-2.lvn6.i386.rpm 
from this website:
[http://fedora.univ-nantes.fr/rpm.livna.org/fedora/development/i386/](http://fedora.univ-nantes.fr/rpm.livna.org/fedora/development/i386/)
and applied to it the command:
sudo alien gsview-4.8-2.lvn6.i386.rpm
This command created the Debian package:
gsview_4.8-3_i386.deb
Then:
sudo dpkg -i gsview_4.8-3_i386.deb

But this is not the end of the story, because I also have to 
configure ghostscript. I find that gsview-4.8 gives the best quality
of font display (crisp fonts) when used with ghostscript 8.15.4.
Installed on Ubuntu is ghostscript 8.61, which apears inferior in
terms of font quality. Therefore I decided to compile the shared object
ghostscript 8.15.4 for the local installation in my home folder:

./configure --prefix=/home/andrei/usr/

I needed to install the following additional packages, for it to
compile:

build-essential libjpeg62-dev zlib1g-dev  libpng  libpng12-dev libgtk1.2-dev libgtk2.0-dev

(not sure about libgtk2.0-dev, if it is needed...)

(not sure is I need libpng, perhaps libpng12-dev would be enough...)
Then I executed:
make so
make soinstall

Now I have to think about fonts. I just copied from the system:

mkdir /home/andrei/usr/share/ghostscript/fonts
cp -a /usr/share/fonts/type1   /home/andrei/usr/share/ghostscript/fonts/

Then I installed it, and run it. In Options -> Advanced Configure 
selected Ghostscript Shared Object:
/home/andrei/usr/lib/libgs.so.8
and included the path:
/home/andrei/usr/share/ghostscript/fonts/type1/gsfonts/
Then it worked, except for resizing lead to a crush complaining about
the unknown paper size a4. I corrected this by going
to Options -> Advanced Configure and entering into Ghostscript Options:
-sPAPERSIZE=letter
This apparently solved the problem...

Andrei.

---

