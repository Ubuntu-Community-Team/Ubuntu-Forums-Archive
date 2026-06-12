---
title: "Compiling issues (pdftohtml)"
date: 2009-06-18
forum: General Help
---

### Post by Daimones on 2009-06-18
Okay have been delving head first into linux over the past few months and have learned a lot just browsing forums for the most part, but now I got a question I can't find an answer to, if anyone could help it would be much appreciated.

I am trying to install pdftohtml, which I can do from the poppler-utils package, but that is an outdated version(0.36), and it leaves me with html files that i can't make do what I want.

I have used the newer version(0.39) on a windows PC and it gives me what I want. So I tried to install 0.39, and 0.40 on my LAMP server and they just won't install. I downloaded the tar ball, extracted it, and here is what I get for each.

Version 0.39
```

plist@MGL-Web:~/pdftohtml-0.39$ ./configure
-bash: ./configure: No such file or directory
plist@MGL-Web:~/pdftohtml-0.39$ make
make[1]: *** [HtmlOutputDev.o] Error 1
make[1]: Leaving directory `/home/plist/pdftohtml-0.39/src'
make: *** [all] Error 2
plist@MGL-Web:~/pdftohtml-0.39$

```

Version 0.40
```

plist@MGL-Web:~/pdftohtml-0.40a$ ./configure
-bash: ./configure: No such file or directory

plist@MGL-Web:~/pdftohtml-0.40a$ make install
mkdir -p /usr/local/bin
/usr/bin/install -c xpdf/pdftops /usr/local/bin/pdftops
/usr/bin/install: cannot stat `xpdf/pdftops': No such file or directory
make: *** [install] Error 1

```

I am new to compiling in linux so not exactly sure if the missing ./configure is a huge deal or not. Neither of the unpacked files contained an install, but 0.39 did contain a readme. All it said about installing was. 

```

How to compile pdftohtml ?
------------------------------

To compile pdftohtml, type :

        make

To compile pdftohtml with debug information and memory leak detection type:

        make DEBUG="-g -DDEBUG_MEM"

This version of pdftohtml was tested on Linux, FreeBSD, Solaris, MacOS X
and Windows


```
](*,)
Any help would be much appreciated, thanks in advance. (If anyone knows a similar program that just does the same as this that would be even better, since I don't think this is supported anymore anyway)

---

### Post by t4thfavor on 2009-06-18
just type make as there is no configure script, I just compiled it on an AMD64 box, and it worked like a charm.
Though  it had a ton of warnings.

Make sure you install the build-essential package thoug, im not sure it will work without it.


EDIT:

I can't get it to install though, the above mentioned version must have been previously installed.

But at least it compiled as it was supposed to.

Just use the binary that ends up in the src directory, and theres no need to install it.

---

### Post by Daimones on 2009-06-18
Did you try "make install"? Make worked fine for version 0.40 for me, not make install though.

Also which version did you try?

Build-essentials is at the newest version.

---

### Post by nothingspecial on 2009-06-18
Try

```
sudo apt-get install build-essential
make
sudo make install
```

---

### Post by t4thfavor on 2009-06-18
.40 I did try "make install" Though I am not trying to install it, just compile it so as to give you some idea why yours did not work.

chance@AMD64:~/pdftohtml-0.40a$ sudo make install
mkdir -p /usr/local/bin
/usr/bin/install -c xpdf/pdftops /usr/local/bin/pdftops
/usr/bin/install: cannot stat `xpdf/pdftops': No such file or directory
make: *** [install] Error 1

I assume you got it going then? 

Im glad to hear that!

---

### Post by Daimones on 2009-06-18
I guess I should've made the title installing issues haha, since that's where I'm having the issues in .40.

0.39 won't compile, but .40 won't install, I'm getting the same error you are getting. Also I have tried to install build-essentials already, it is saying it's up to date.

---

### Post by t4thfavor on 2009-06-18
Just use the binary in the src folder after compile. You can run it by doing:

cd src
./pdftohtml -v

It should read

pdftohtml version 0.40 [http://pdftohtml.sourceforge.net/](http://pdftohtml.sourceforge.net/), based on Xpdf version 3.01
Copyright 1999-2003 Gueorgui Ovtcharov and Rainer Dorsch
Copyright 1996-2005 Glyph & Cog, LLC

Usage: pdftohtml [options] <PDF-file> [<html-file> <xml-file>]
  -f <int>          : first page to convert
  -l <int>          : last page to convert
  -q                : don't print any messages or errors
  -h                : print usage information
  -help             : print usage information
  -p                : exchange .pdf links by .html
  -c                : generate complex document
  -i                : ignore images
  -noframes         : generate no frames
  -stdout           : use standard output
  -zoom <fp>        : zoom the pdf document (default 1.5)
  -xml              : output for XML post-processing
  -hidden           : output hidden text
  -enc <string>     : output text encoding name
  -dev <string>     : output device name for Ghostscript (png16m, jpeg etc)
  -v                : print copyright and version info
  -opw <string>     : owner password (for encrypted files)
  -upw <string>     : user password (for encrypted files)


then you just have to do ./pdftohtml Path/To/PDF /Path/To/HTML


EDIT:

Im not too keen on c++ so im not sure about .39, but I think it has a source error. The devs are just not that great at calling out errors with useful information.

---

### Post by Daimones on 2009-06-18
Sorry for late response, left work. Just gave it a shot running it out of the src dir, and it ran perfect!! Would there be anyway to manually enter it into bash so I can run it from anywhere via pdftohtml?

Suppose it's probably just a script named pdftohtml, in the bin dir which runs the ./src/pdftohtml?

Thx for the help!

---

### Post by Daimones on 2009-06-19
Still having some issues if you could maybe help me. The problem is that I'm trying to run this program from a php website. It's working from ubuntu shell, but whenever I try to run it from the website, mozilla starts eating up memory and freezes.

Is there anyway to either force this to install, or get it into a bash script to try it, problem is the website sends arguments and I don't know how to handle those in a bash script nor do I know if that is going to solve the problem.

---

### Post by Daimones on 2009-06-19
Shameless bump for someone that can make .39 compile](*,)

---

### Post by Satish Chauhan on 2011-01-19
I hope below mentioned steps will help you.

wget [http://sourceforge.net/projects/pdftohtml/files/Experimental%20Versions/pdftohtml%200.40/pdftohtml-0.40a.tar.gz/download](http://sourceforge.net/projects/pdftohtml/files/Experimental%20Versions/pdftohtml%200.40/pdftohtml-0.40a.tar.gz/download)
wget [ftp://ftp.foolabs.com/pub/xpdf/xpdf-3.02.tar.gz](ftp://ftp.foolabs.com/pub/xpdf/xpdf-3.02.tar.gz)

tar -xf /home/satish/pdftohtml-0.40a.tar.gz
tar -xf /home/satish/xpdf-3.02.tar.gz

cd /home/satish/xpdf-3.02
./configure
make

cd /home/satish/pdftohtml-0.40a
make

mv/cp /home/satish/pdftohtml-0.40a/xpdf /home/satish/pdftohtml-0.40a/xpdf-old

mv/cp /home/satish/xpdf-3.02/xpdf /home/satish/pdftohtml-0.40a/xpdf
mv/cp /home/satish/xpdf-3.02/doc /home/satish/pdftohtml-0.40a/doc

cd /home/satish/pdftohtml-0.40a
make install

/usr/bin/install -c ./src/pdftohtml /usr/local/bin/pdftohtml

---

### Post by Martin Seroczynski on 2011-04-30
I've encountered also problems while compiling the xpdf library, what I needed to do is:

1. Install lesstif2 and lesstif2-dev packages
2. configure xpdf with:
./configure --prefix=/usr --with-freetype2-includes=/usr/include/freetype2 --with-Xm-includes=/usr/include/Xm/ --with-Xm-library=/usr/lib/

and then proceed with Satish instructions.

---

