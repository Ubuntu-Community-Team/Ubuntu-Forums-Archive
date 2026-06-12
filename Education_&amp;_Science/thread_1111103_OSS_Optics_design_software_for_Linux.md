---
title: "OSS Optics design software for Linux"
date: 2009-03-30
forum: Education &amp; Science
---

### Post by AlexVader on 2009-03-30
Hi Forum...

I wonder... is there any package out there that will perform raytracing analysis, gaussian beam propagation and aberration analysis for an optical assembly...?

Some sort of Code V, [http://www.opticalres.com/](http://www.opticalres.com/) , but OpenSource...?


Thanks in advance

Alex

---

### Post by hubie on 2009-04-01
For what it's worth, I successfully run ZEMAX on a virtual PC by running VMWare Workstation on my 64-bit Ubuntu box.  The only glitches I get are related to that damn hardware (USB) key needed to run the code, where the virtual PC doesn't see the key unless I do it right.

A free possibility, though one I have not tried myself, is [opus]("http://www.maxreason.com/software/optics/opus.html").  I think I'll have to try it out myself.  It runs on top of [XBasic]("http://www.xbasic.org/"), so you'll need to install that as well.

---

### Post by AlexVader on 2009-04-01
Hi Hubie

Thx a Lot, but just tell me.. is XBasic an interpreter, or a compiler...?

I have installed Gambas, but I guess it won't compile OPUS source...

And I would like to build an exec for 64 bit arch....  so is XBasic some sort of script interpreter ( slow like hell ) like Python, or can it take full advantage of the OS features by building an exec...? 

Best Regards

Alex

---

### Post by hubie on 2009-04-01
I'm sorry to say that I can't tell you anything about XBasic.  When I saw your original post I started Googling around looking for some very nice C code that I had downloaded about nine years ago that did pretty much what you were asking.  It was command-line driven.  I recall that it came from a professor at (and this is where my memory gets fuzzy) Stanford or one of the California schools.  I remembered it because it was simple code that easily compiled on a Sun station I was using.  I played around with it for a bit then put it aside.  Unfortunately that Sun machine is long gone as is the code I downloaded.

In any event, I was trying to see if I could find the code through Google and I came across that other page.  I was impressed with his web site and the features that his code had, so I passed that info on to you.  I am intrigued enough to try it out, so I will let you know what I find.

I'm still looking for the original code I mentioned because now it is bugging me and I want to dig it back up.  If I do, I'll post here what I find.

---

### Post by AlexVader on 2009-04-01
Hi Hubie.

So, I have downloaded this XBasic thing ( the binaries ) and untarred it in /, my OS is 64 bits, and I have 32 bits compat layer, so I downloaded the src from XBasic to build a 64 bit compiler... so as to build a 64 bit Opus... man... How does one compile XBasic from source...? I cd into the dir of XBasic source, type make and shell reports that.. 

alex@iskandhar:~/Desktop/xbasic-6.3.0$ make
make: *** No rule to make target `linux/lib/xstart.o', needed by `bin/xb'.  Stop.
alex@iskandhar:~/Desktop/xbasic-6.3.0$ 


If compiling XBasic from source is difficult, i wonder how will it be compiling Opus to 64 bits arch...   :-(

Best regards

Alex

---

### Post by hubie on 2009-04-03
It appears as though the version of XBasic that you download from the XBasic site does not compile under recent versions of gcc.  [There is a page]("http://gnetools.sourceforge.net/xbsupport/index.html"), linked from the XBasic site, where someone is continuing development and has versions to download.  You might want to give that a look.

I'll probably give it all a try as well, but I don't think I'll be able to get to it for several weeks.

---

### Post by Lorne L. Reap on 2010-06-12
This works for Ubuntu 9.10, so just Google the XBasic RPM and download to your home directory.
To run the program type xb in term!

~$ sudo alien -d xbasic-6.2.3-1.i386.rpm

Lorne

---

