---
title: "Compiling Antiword 0.37"
date: 2006-06-15
forum: Desktop Environments
---

### Post by mbeach on 2006-06-15
Hi,

I have Antiword (ver 0.35-2sarge1) installed, but I want to use some features in version 0.37.  I've tried using 'make' on the source code downloaded at both:
[https://launchpad.net/distros/ubuntu/+source/antiword/0.37-1](https://launchpad.net/distros/ubuntu/+source/antiword/0.37-1)
and 
[http://www.winfield.demon.nl/](http://www.winfield.demon.nl/)

but I get several errors and I'm not really sure where to start trying to resolve them.  Anyway, I was wondering if anyone knows of a .deb package in existance for Antiword 0.37, or could provide me with the details of their success story in compiling the source.

Thanks,
mb.

---

### Post by mbeach on 2006-06-15
nevermind - got one here:
[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fa%2Fantiword%2Fantiword_0.37-1_i386.deb&md5sum=a305476ae05aa4a009600645ca997107&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fa%2Fantiword%2Fantiword_0.37-1_i386.deb&md5sum=a305476ae05aa4a009600645ca997107&arch=i386&type=main)

---

### Post by lukjad on 2007-08-05
Pardon me but none of the links work. Would anyone else have any other links, tips, etc. Here is the message that I got after trying to make the 0.37 version.

lukjad007@stationx:~/Desktop/antiword-0.37$ make
gcc -Wall -pedantic -O2 -DNDEBUG -c main_u.c
gcc -Wall -pedantic -O2 -DNDEBUG -c asc85enc.c
gcc -Wall -pedantic -O2 -DNDEBUG -c blocklist.c
gcc -Wall -pedantic -O2 -DNDEBUG -c chartrans.c
gcc -Wall -pedantic -O2 -DNDEBUG -c datalist.c
gcc -Wall -pedantic -O2 -DNDEBUG -c depot.c
gcc -Wall -pedantic -O2 -DNDEBUG -c dib2eps.c
gcc -Wall -pedantic -O2 -DNDEBUG -c doclist.c
gcc -Wall -pedantic -O2 -DNDEBUG -c fail.c
gcc -Wall -pedantic -O2 -DNDEBUG -c finddata.c
gcc -Wall -pedantic -O2 -DNDEBUG -c findtext.c
gcc -Wall -pedantic -O2 -DNDEBUG -c fmt_text.c
gcc -Wall -pedantic -O2 -DNDEBUG -c fontlist.c
gcc -Wall -pedantic -O2 -DNDEBUG -c fonts.c
gcc -Wall -pedantic -O2 -DNDEBUG -c fonts_u.c
gcc -Wall -pedantic -O2 -DNDEBUG -c hdrftrlist.c
gcc -Wall -pedantic -O2 -DNDEBUG -c imgexam.c
gcc -Wall -pedantic -O2 -DNDEBUG -c imgtrans.c
gcc -Wall -pedantic -O2 -DNDEBUG -c jpeg2eps.c
gcc -Wall -pedantic -O2 -DNDEBUG -c listlist.c
gcc -Wall -pedantic -O2 -DNDEBUG -c misc.c
gcc -Wall -pedantic -O2 -DNDEBUG -c notes.c
gcc -Wall -pedantic -O2 -DNDEBUG -c options.c
gcc -Wall -pedantic -O2 -DNDEBUG -c out2window.c
gcc -Wall -pedantic -O2 -DNDEBUG -c output.c
gcc -Wall -pedantic -O2 -DNDEBUG -c pdf.c
gcc -Wall -pedantic -O2 -DNDEBUG -c pictlist.c
gcc -Wall -pedantic -O2 -DNDEBUG -c png2eps.c
gcc -Wall -pedantic -O2 -DNDEBUG -c postscript.c
gcc -Wall -pedantic -O2 -DNDEBUG -c prop0.c
gcc -Wall -pedantic -O2 -DNDEBUG -c prop2.c
gcc -Wall -pedantic -O2 -DNDEBUG -c prop6.c
gcc -Wall -pedantic -O2 -DNDEBUG -c prop8.c
gcc -Wall -pedantic -O2 -DNDEBUG -c properties.c
gcc -Wall -pedantic -O2 -DNDEBUG -c propmod.c
gcc -Wall -pedantic -O2 -DNDEBUG -c rowlist.c
gcc -Wall -pedantic -O2 -DNDEBUG -c sectlist.c
gcc -Wall -pedantic -O2 -DNDEBUG -c stylelist.c
gcc -Wall -pedantic -O2 -DNDEBUG -c stylesheet.c
gcc -Wall -pedantic -O2 -DNDEBUG -c summary.c
gcc -Wall -pedantic -O2 -DNDEBUG -c tabstop.c
gcc -Wall -pedantic -O2 -DNDEBUG -c text.c
gcc -Wall -pedantic -O2 -DNDEBUG -c unix.c
gcc -Wall -pedantic -O2 -DNDEBUG -c utf8.c
gcc -Wall -pedantic -O2 -DNDEBUG -c word2text.c
gcc -Wall -pedantic -O2 -DNDEBUG -c worddos.c
gcc -Wall -pedantic -O2 -DNDEBUG -c wordlib.c
gcc -Wall -pedantic -O2 -DNDEBUG -c wordmac.c
gcc -Wall -pedantic -O2 -DNDEBUG -c wordole.c
gcc -Wall -pedantic -O2 -DNDEBUG -c wordwin.c
gcc -Wall -pedantic -O2 -DNDEBUG -c xmalloc.c
gcc -Wall -pedantic -O2 -DNDEBUG -c xml.c
gcc  main_u.o asc85enc.o blocklist.o chartrans.o datalist.o depot.o dib2eps.o doclist.o fail.o finddata.o findtext.o fmt_text.o fontlist.o fonts.o fonts_u.o hdrftrlist.o imgexam.o imgtrans.o jpeg2eps.o listlist.o misc.o notes.o options.o out2window.o output.o pdf.o pictlist.o png2eps.o postscript.o prop0.o prop2.o prop6.o prop8.o properties.o propmod.o rowlist.o sectlist.o stylelist.o stylesheet.o summary.o tabstop.o text.o unix.o utf8.o word2text.o worddos.o wordlib.o wordmac.o wordole.o wordwin.o xmalloc.o xml.o  -o antiword


Well then, that's that. I'll install the repository version until I figure out how to work this out.

Thanks, 

Luke.

---

