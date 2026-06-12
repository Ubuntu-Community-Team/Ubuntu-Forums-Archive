---
title: "How to build xv on Ubuntu or Debian - help"
date: 2009-06-16
forum: General Help
---

### Post by jimmy7430 on 2009-06-16
Initially, I request for one file in this help post:
[http://bok.fas.harvard.edu/debian/xv/xv-3.10a-jumbo20050501-1.diff.gz](http://bok.fas.harvard.edu/debian/xv/xv-3.10a-jumbo20050501-1.diff.gz) [**this hostname does not resolve as of 2009-05-20]** 
 
This file was referred by several how-to files, one of them is: [http://www.halibutdepot.org/xv/building_xv_on_ubuntu.html](http://www.halibutdepot.org/xv/building_xv_on_ubuntu.html) (I also copy the content of the site above at the bottom of this post)

With a great help from **John Girash**, the sysadmin of server I was trying to access[FONT=monospace], I obtained the missing file. I now upload the file in the second post, so that more people could have and share it. 

[/FONT]   > **How to build xv on Ubuntu or Debian**
initially written 2008-06-26
last modified 2009-05-20
 
**Files Needed:**

[ftp://ftp.cis.upenn.edu/pub/xv/xv-3.10a.tar.gz](ftp://ftp.cis.upenn.edu/pub/xv/xv-3.10a.tar.gz)
[http://dfn.dl.sourceforge.net/sourceforge/png-mng/xv-3.10a-jumbo-patches-20070520.tar.gz](http://dfn.dl.sourceforge.net/sourceforge/png-mng/xv-3.10a-jumbo-patches-20070520.tar.gz)
[http://bok.fas.harvard.edu/debian/xv/xv-3.10a-jumbo20050501-1.diff.gz](http://bok.fas.harvard.edu/debian/xv/xv-3.10a-jumbo20050501-1.diff.gz) [**this hostname does not resolve as of 2009-05-20]** 

**Abstract:**

The last official release of the venerable image editor xv was xv-3.10a, dated 1994-12-29.

The author ceased maintaining xv in 1994, and yet the software remains popular today. Why, then, do so few distributions ship with a packaged version of xv? It turns out that the code, now 14 years old, suffers from a number of known security vulnerabilities. While present-day developers now actively maintain a patchset against the last official release, the xv license forbids distribution of these modified versions.

(Quoting from the xv license: "The software may be modified for your own purposes, but modified versions may not be distributed without prior consent of the author.")

If you want to use a modern version of xv, then you must either use a source-based distribution like Gentoo, or you must patch the ancient xv source release and build the patched version yourself.

**How to build xv on Ubuntu or Debian:**

We must grab the sources and packages, install the build-time dependencies, build xv, and then install it. In this demonstration, we start with a fresh installation of Ubuntu "Hardy Heron" (08.04) with updates installed as of 2008-06-26 . The same procedure also works on the "testing" release of Debain as of 2008-06-26 .

For the purposes of our demonstration, we become root right away ("sudo su -") and keep using that root shell for the rest of the steps. This is bad practice; you should consider using a regular account for most of the steps and manually running the commands that require root priviledges (like apt-get and dpkg) via sudo.

**user@ubuntu:~$** sudo su -
**[sudo] password for user:** 
**root@ubuntu:~#** 

Install the following packages:

**root@ubuntu:~#** apt-get install patch libx11-dev libc6-dev libtiff-dev zlib-bin zlibc libpng3 libpng12-dev libpng12-0 zlib1g zlib1g-dev libjpeg62-dev libtiff4-dev libtiff4 libjasper-dev libxt-dev

(Optional.) In order to assemble the xv binaries into a Debian package file, we must install the following packages:

**root@ubuntu:~#** apt-get install dpkg-dev debhelper build-essential

Although we create a Debian package later, it isn't strictly necessary. We could make do with copying the xv binaries that we'll build to some reasonable location like /usr/local/bin/ . If you choose this route, then find & copy the xv binaries, and ignore the sections about building a Debian package file.

Now we can begin unpacking and patching the xv source:

**root@ubuntu:~#** mkdir xv-build

**root@ubuntu:~#** cd xv-build/

**root@ubuntu:~/xv-build#** wget [ftp://ftp.cis.upenn.edu/pub/xv/xv-3.10a.tar.gz](ftp://ftp.cis.upenn.edu/pub/xv/xv-3.10a.tar.gz) [http://dfn.dl.sourceforge.net/sourceforge/png-mng/xv-3.10a-jumbo-patches-20070520.tar.gz](http://dfn.dl.sourceforge.net/sourceforge/png-mng/xv-3.10a-jumbo-patches-20070520.tar.gz) [http://bok.fas.harvard.edu/debian/xv/xv-3.10a-jumbo20050501-1.diff.gz](http://bok.fas.harvard.edu/debian/xv/xv-3.10a-jumbo20050501-1.diff.gz)

**root@ubuntu:~/xv-build#** ls -1
xv-3.10a-jumbo20050501-1.diff.gz
xv-3.10a-jumbo-patches-20070520.tar.gz
xv-3.10a.tar.gz

**root@ubuntu:~/xv-build#** gunzip xv-3.10a-jumbo20050501-1.diff.gz

**root@ubuntu:~/xv-build#** tar xfvz xv-3.10a.tar.gz

**root@ubuntu:~/xv-build#** tar xfvz xv-3.10a-jumbo-patches-20070520.tar.gz

**root@ubuntu:~/xv-build#** cd xv-3.10a

**root@ubuntu:~/xv-build/xv-3.10a#** patch -p1 < ../xv-3.10a-jumbo-fix-enh-patch-20070520.txt

**root@ubuntu:~/xv-build/xv-3.10a#** patch -p1 < ../xv-3.10a-jumbo20050501-1.diff

NOTE: This patch produces rejects in Makefile.  xv still builds correctly, so ignore them.

The Makefile will need to use sane LSB paths like /usr/lib/ instead of /usr/local/lib/ .  Modify the Makefile as shown below.

(In this example, you can copy-and-paste the below text into a patch called Makefile.ubuntu.diff).

**root@ubuntu:~/xv-build/xv-3.10a#** cat > Makefile.ubuntu.diff

--- xv-3.10a/Makefile.original.jrt      2008-07-09 19:58:01.000000000 -0400
+++ xv-3.10a/Makefile   2008-07-09 20:00:14.000000000 -0400
@@ -125,7 +125,8 @@
 JPEGINC = -I$(JPEGDIR)/include
 #JPEGINC = -I$(JPEGDIR)
 ###
-JPEGLIB = -L$(JPEGDIR)/lib -ljpeg
+#JPEGLIB = -L$(JPEGDIR)/lib -ljpeg
+JPEGLIB = -L$(JPEGDIR)/lib/libjpeg.a
 #JPEGLIB = -L$(JPEGDIR) -ljpeg
 #JPEGLIB = $(JPEGDIR)/libjpeg.a
 ###
@@ -179,10 +180,10 @@
 JP2K    = -DDOJP2K
 ###
 #JP2KDIR = ../../jasper
-JP2KDIR = /usr/local/lib
+JP2KDIR = /usr/lib
 ###
 #JP2KINC = -I$(JP2KDIR)
-JP2KINC = -I/usr/local/include
+JP2KINC = -I/usr/include
 ###
 #JP2KLIB = -L$(JP2KDIR) -ljasper
 JP2KLIB = $(JP2KDIR)/libjasper.a

(hit **control-D** to end the file)

**root@ubuntu:~/xv-build/xv-3.10a#** patch -p1 < Makefile.ubuntu.diff

At this point, the xv binaries are ready to be built. If you don't care about making a Debian package, then you can run make and then copy the binaries and stop here:

**root@ubuntu:~/xv-build/xv-3.10a#** cp {xv,vdcomp,bggen,xvpictoppm,xcmap} /usr/local/bin/

But let's do this the right way and make a proper Debian package:

**root@ubuntu:~/xv-build/xv-3.10a#** chmod 755 debian/rules

**root@ubuntu:~/xv-build/xv-3.10a#** dpkg-buildpackage -uc -b

**root@ubuntu:~/xv-build/xv-3.10a#** cd ..

**root@ubuntu:~/xv-build#** dpkg -i xv_3.10a-jumbo20050501-1_i386.deb

**root@ubuntu:~/xv-build#** dpkg -i xv-doc_3.10a-jumbo20050501-1_all.deb

**root@ubuntu:~/xv-build#** cd ..

**root@ubuntu:~#** rm -rf xv-build/

**Acknowledgments:**
I didn't come up with the following procedure on my own. I used the following resources and adapted their suggestions to fit an Ubuntu "Hardy" system:

[http://blog.trivadis.com/blogs/yannneuhaus/archive/2007/09/19/xv-an-image-viewer-quot-on-ubuntu-7-04.aspx](http://blog.trivadis.com/blogs/yannneuhaus/archive/2007/09/19/xv-an-image-viewer-quot-on-ubuntu-7-04.aspx)
[http://bok.fas.harvard.edu/debian/xv/index.html](http://bok.fas.harvard.edu/debian/xv/index.html)
[http://sonic.net/~roelofs/greg_xv.html]("http://sonic.net/%7Eroelofs/greg_xv.html")
[http://www.gregroelofs.com/greg_xv.html](http://www.gregroelofs.com/greg_xv.html)




---

### Post by jimmy7430 on 2009-06-16
With special thanks to **John Girash**, I uploaded the file which was hosted at: 
[http://bok.fas.harvard.edu/debian/xv/](http://bok.fas.harvard.edu/debian/xv/)

The acknowledged author of the files is** Jean Tourrilhes***.*

---

### Post by rbc on 2009-06-16
Is there a reason you need to install it from source? It is already available through synaptic, at least it is in Jaunty

---

### Post by jonobr on 2009-06-16
It appears you can get the jumbo patches on sourceforge

[http://prdownloads.sourceforge.net/png-mng/xv-3.10a-jumbo-patches-20050501.tar.gz](http://prdownloads.sourceforge.net/png-mng/xv-3.10a-jumbo-patches-20050501.tar.gz)

---

### Post by jimmy7430 on 2009-06-16
> **rbc said:**
> Is there a reason you need to install it from source? It is already available through synaptic, at least it is in Jaunty

rbc, you may confuse the John Bradley's graphic program **xv** with **xviewer** (X-Windows manager) in debian/ubuntu.  
 
**XV**'s very strange licence, which doesn't allow the modified src to be re-distributed. (obviously, the author thought his original code is perfect enough, but it's actually not. Bugs are here and there.) Due to this reason, it's generally not included in most default linux package.  And other programmers end up with all kinds of patches. 
 
That's the story as far as I know.

---

### Post by jimmy7430 on 2009-06-16
> **jonobr said:**
> It appears you can get the jumbo patches on sourceforge

[http://prdownloads.sourceforge.net/png-mng/xv-3.10a-jumbo-patches-20050501.tar.gz](http://prdownloads.sourceforge.net/png-mng/xv-3.10a-jumbo-patches-20050501.tar.gz)

Yes, you are right.  This patch is for multi-format support. 

The patch with broken link is for bugs.

---

### Post by sblinnikov on 2009-07-26
I've  found that Makefile.ubuntu.diff does not work (PREFIX is not corrected, and spaces are not visible giving a "malformed" message)
Use this as Makefile.ubuntu.diff:
```

--- xv-3.10a/Makefile.original    2009-07-26 14:27:48.000000000 +0400
+++ xv-3.10a/Makefile    2009-07-26 14:33:08.000000000 +0400
@@ -56,7 +56,7 @@
 ### NOTE: Users of old K&R compilers (i.e., any version not supporting C89
 ### string concatenation, such as "fub" "ar" => "fubar") should update
 ### xvtext.c:1831 (or thereabouts) if either PREFIX or DOCDIR changes:
-PREFIX = /usr/local
+PREFIX = /usr
 BINDIR = $(PREFIX)/bin
 MANDIR = $(PREFIX)/share/man/man1
 MANSUF = 1
@@ -125,7 +125,8 @@
 JPEGINC = -I$(JPEGDIR)/include
 #JPEGINC = -I$(JPEGDIR)
 ###
-JPEGLIB = -L$(JPEGDIR)/lib -ljpeg
+#JPEGLIB = -L$(JPEGDIR)/lib -ljpeg
+JPEGLIB = -L$(JPEGDIR)/lib/libjpeg.a
 #JPEGLIB = -L$(JPEGDIR) -ljpeg
 #JPEGLIB = $(JPEGDIR)/libjpeg.a
 ###
@@ -179,10 +180,10 @@
 JP2K    = -DDOJP2K
 ###
 #JP2KDIR = ../../jasper
-JP2KDIR = /usr/local/lib
+JP2KDIR = /usr/lib
 ###
 #JP2KINC = -I$(JP2KDIR)
-JP2KINC = -I/usr/local/include
+JP2KINC = -I/usr/include
 ###
 #JP2KLIB = -L$(JP2KDIR) -ljasper
 JP2KLIB = $(JP2KDIR)/libjasper.a

```

Also attached.

---

### Post by janeman on 2009-08-22
Hello everybody,

I just tried to install xv on my ubuntu 9.04 system but without succsess. When I run "make" there are a lot of errors like

```
xv.c:4692: Fehler: expected »;« before »resAtom«
xv.c:4695: Warnung: Implizite Deklaration der Funktion »XrmInitialize«
xv.c:4697: Fehler: »XrmDatabase« nicht deklariert (erste Benutzung in dieser Funktion)
xv.c:4697: Fehler: expected »;« before numeric constant
xv.c:4705: Fehler: »resAtom« nicht deklariert (erste Benutzung in dieser Funktion)
xv.c:4705: Fehler: »theDisp« nicht deklariert (erste Benutzung in dieser Funktion)
xv.c:4705: Fehler: »True« nicht deklariert (erste Benutzung in dieser Funktion)
xv.c:4706: Fehler: »None« nicht deklariert (erste Benutzung in dieser Funktion)
xv.c:4707: Fehler: expected »;« before »actType«
xv.c:4712: Fehler: »spec_window« nicht deklariert (erste Benutzung in dieser Funktion)
xv.c:4714: Fehler: »False« nicht deklariert (erste Benutzung in dieser Funktion)
xv.c:4715: Fehler: »XA_STRING« nicht deklariert (erste Benutzung in dieser Funktion)
xv.c:4715: Fehler: »actType« nicht deklariert (erste Benutzung in dieser Funktion)
xv.c:4723: Fehler: »Success« nicht deklariert (erste Benutzung in dieser Funktion)
xv.c:4737: Warnung: Implizite Deklaration der Funktion »XrmGetStringDatabase«
xv.c:4747: Warnung: Implizite Deklaration der Funktion »XResourceManagerString«
xv.c:4747: Warnung: Zuweisung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
xv.c:4756: Fehler: expected »;« before »res1«
xv.c:4766: Warnung: Implizite Deklaration der Funktion »XrmGetFileDatabase«
xv.c:4778: Fehler: »res1« nicht deklariert (erste Benutzung in dieser Funktion)
xv.c:4787: Warnung: Implizite Deklaration der Funktion »XrmMergeDatabases«
xv.c:4801: Warnung: Unverträgliche implizite Deklaration der eingebauten Funktion »strcpy«
xv.c:4802: Warnung: Unverträgliche implizite Deklaration der eingebauten Funktion »strcat«
xv.c:4809: Warnung: Implizite Deklaration der Funktion »XrmGetResource«
xv.c:4809: Fehler: »result« nicht deklariert (erste Benutzung in dieser Funktion)
make[1]: *** [xv.o] Fehler 1
make[1]: Verlasse Verzeichnis '/home/jan/xv-build1/xv-3.10a'
make: *** [build-stamp] Fehler 2
```

I am quite new to all this, so I hope you can give me some hints. Do I have to adjust something to my installation?

Thanks in advance!

Jan

---

### Post by zim2dive on 2011-01-23
I'm trying this with 10.04 and get this error ```
xvtiff.c:2151: warning: passing argument 2 of &#8216;strcpy&#8217; makes pointer from integer without a cast
/usr/include/bits/string3.h:105: note: expected &#8216;const char * __restrict__&#8217; but argument is of type &#8216;int&#8217;
make: *** [xvtiff.o] Error 1
```
any ideas?

EDIT: I found I needed to install the dev versions of libtiff and jasper.

---

