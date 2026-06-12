---
title: "EPSXE Ubuntu"
date: 2013-10-30
forum: Gaming &amp; Leisure
---

### Post by adec2 on 2013-10-30
Hi, I've just updated to ubuntu 13.10 now when running epsxe i get this error in the terminal

"./epsxe: error while loading shared libraries: libSDL_ttf-2.0.so.0: cannot open shared object file: No such file or directory"

It is already installed in /usr/lib/x86_64-linux-gnu

Can anyone help please?

 ***************Edit Never mind i've sorted it myself. I was missing ia32 package and followed this to fix it for me*************

Install Synaptic from terminal window

 sudo apt-get install synaptic

 Launch synaptic and goto &#8220;settings > Repositories&#8221;

 click &#8220;other software > add&#8221;

 insert this line in the box "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring main restricted universe multiverse"

 click ok and close synaptic

 in terminal &#8220;sudo apt-get update&#8221;

 in terminal &#8220;sudo apt-get install ia32-libs&#8221;

It also worked for getting the emulator daphne (laserdisc emulator) working too. Hope it helps others :)

---

### Post by oldrocker99 on 2013-10-30
I had wondered how to install is32-libs in 13.10 myself. Thanks!

---

