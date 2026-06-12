---
title: "VESTA (a 3D Visualization System for Electronic and Structural Analysis) Install"
date: 2008-06-25
forum: Education &amp; Science
---

### Post by NetFreeDiver on 2008-06-25
Hello everybody,

I was trying to install VESTA ([http://www.geocities.jp/kmo_mma/crystal/en/vesta.html](http://www.geocities.jp/kmo_mma/crystal/en/vesta.html)) on ubuntu. Installation part is really easy, just extracting files. But the problem comes with running.

When I start VESTA it gives me the error:

VESTA: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

I searched for the tiff libraries and I found that hardy heron has libtiff4. When I searched for all packages from web I could not find libtiff.so.3.

Long story short, I am in trouble :)

Can you help me?

ciao

---

### Post by NetFreeDiver on 2008-06-25
Sorry for taking your time. I found the answer on a web page, which is


The solution:

You have to make so that the system to use the newer tiff library.

For the purpose you have to go in the following directory: /usr/lib by using cd /usr/lib/

Then just link the libtiff.so.4 library with the libtiff.so.3 one. Just type the following:

ln -s libtiff.so.4 libtiff.so.3


Thanks,

ciao

---

### Post by mjcomps on 2008-08-14
What is the procedure of the installation? I'm dont understand the procedure description in the VESTA_manual.pdf.

---

### Post by memcbr on 2009-06-03
I'm a new user trying to install VESTA and don't see VESTA_manual.pdf anywhere in the installation package. Where can I find installation instructions? Thanks!

---

### Post by Dusty Fairmount on 2010-09-26
The PDF manual is in the documentation tab on the VESTA homepage.

However, the PDF manual simply states that the tar.bz2 files should be extracted to a folder.  Then to run VESTA, just double click on the file.  But nothing happens when I double click on the file.  

p.s. I am a brand new convert to Linux (4 hours ago) and I don't know much :)

---

