---
title: "Installing Modnum with Scicoslab"
date: 2011-04-17
forum: Education &amp; Science
---

### Post by skippylou on 2011-04-17
I am having problems installing Modnum for use with Scicoslab.

I am using Ubuntu 10.4 LTS 64 bit for AMD processor.

First I tried Scicoslab 4.4.1 (scicoslab-gtk_4.4.1-1_amd64.maverick.deb) and Modnum 4.2.2. When I run Scicoslab, it complains that Modnum was compiled with Scicoslab 4.4 beta 7.

So, I remove 4.4.1 and install 4.4 beta 7.  Now I get this message when I launch scicoslab:

Startup execution:
  loading initial environment
... Search Scilab version ...
Version of ScicosLab is : 4.4b7
Version of Scicos is : scicos4.4
/home/skippy/modnum_422//interf/scicoslab/../../src/libmodnum_lib.so: wrong ELF class: ELFCLASS32
"/../../src/libmodnum_lib.so")
                               !--error 236
link: the shared archive was not loaded
at line      55 of exec file called by :   
  exec(MODNUM+"/interf/scicoslab/loader.sce");
at line      16 of exec file called by :   
      exec(startup,-1);mclose(startup)
at line     272 of exec file called by :   
exec('SCI/scilab.star',-1);;quit

So I try "./configure --with-scisrc=/usr/lib64/scicoslab-gtk-4.4b7" followed by "make all" gives pages of error messages.

Can you suggest which version of Scicoslab and which version of Modnum will be compatible?

Any help or suggestions would be greatly appreciated.

Skippy

---

