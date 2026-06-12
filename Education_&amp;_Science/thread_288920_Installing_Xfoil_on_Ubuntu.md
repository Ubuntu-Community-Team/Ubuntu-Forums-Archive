---
title: "Installing Xfoil on Ubuntu"
date: 2006-10-30
forum: Education &amp; Science
---

### Post by Icarosaurus on 2006-10-30
Anyone can tell me how to compile Xfoil on Ubuntu Dapper?
Modifying Makefiles is a bit hard for a beginner :)
Thank you...
**EDIT**
I was able to make a 32 bit deb package of Xfoil 6.97.
Download it from the attachment and send me comments and suggestions!
Updated Versions of my package are here:
[http://giuschet.altervista.org/Ubuntu/]("http://giuschet.altervista.org/Ubuntu/")
[Here]("http://ubuntuforums.org/showpost.php?p=6262083&postcount=1") are the instructions for compiling it by yourself.
Visit my [blog]("http://giuseppeschettini.wordpress.com/") too for news :)

**Instructions for making the 32 bit package work in a 64 bit environment (untill I'll release a 64 bit version)**

- Download the package and, in a terminal, in the same directory of the package:
```

sudo dpkg -i --force-architecture xfoil_6.97-1_i386.deb

```

-Be sure you installed the 32 bit compatibility libraries (ia32-libs)

-The program needs the 32 bit version of the libg2c0 library...download it from [here]("http://packages.ubuntu.com/search?arch=i386&searchon=names&keywords=libg2c0").

-In the same directory of the libg2c0 package open a terminal:
```

dpkg -x xfoil_6.97-1_i386.deb .
sudo cp usr/lib/libg2c* /usr/lib32/
rm -r usr

```

-typing xfoil anywhere in the terminal should start the program

---

### Post by danb2 on 2006-11-15
yes I am experiencing the same result. The directions are not quite right or something. 

So far I have been attempting to follow directions in the readme files. 

As directed I went to the orr directory and corrected the neccesary files but when I did 
 %make osgen but I am not sure it went correctly. Although I did not get an obvious error. 
Then I did the 
%make osmap.o but I am not sure anything happened. 
then out of frustration I just did
%make instead of %make osgen and the normal process seemed to unfold on the screen.
I then retried 
%make osmap.o and the msg was something like osmap.o is up to date

once in the plotlib directory, I used 
%pwd results to edit the plotlib makefile plus I commented out the "include./config.make" line for better of worse at least the 
%make libPlt.a appeared to work.

I ran XFOIL in the runs directory as suggested and it appeared to run.


Could you post here if there is something you figured out I will do the same.

Dan

---

### Post by parktownprawn on 2006-11-15
i know nothing about xfoil but the first hit from google gave me: 

------------

How to get xfoil running in Ubuntu (or probably any Debian variant)

Download the code:
[http://raphael.mit.edu/xfoil/xfoil694.tar.gz](http://raphael.mit.edu/xfoil/xfoil694.tar.gz)

Extract it to a convenient location.  Follow the instructions in the README.  You may run into the same issue I had during compiling:

g77 -o xfoil xfoil.o xpanel.o xoper.o xtcam.o xgdes.o xqdes.o xmdes.o xsolve.o x bl.o xblsys.o xpol.o xplots.o xgeom.o xutils.o modify.o polplt.o aread.o naca.o spline.o plutil.o iopol.o gui.o sort.o dplot.o profil.o userio.o ../plotlib/libP lt.a  -L/usr/X11R6/lib -lX11 -lblas-3
/usr/bin/ld: cannot find -lblas-3
collect2: ld returned 1 exit status
make: *** [xfoil] Error 1

This can be solved by installing the following packages (not exactly sure which one solved it, but I installed them all for good measure.)

lapack3, lapack3-dev, lapack3-doc, refblas3, refblas3-dev, refblas3-doc

The program should then compile with out any complaints.  The executable will be located in your ./bin directory.  

------------------------
from 

[http://noah-hicks.blogspot.com/](http://noah-hicks.blogspot.com/)

---

### Post by Icarosaurus on 2006-11-15
Oh...thank you guys for your posts, I'll try to compile Xfoil as soon as I can, following your suggestions.
I hope our attempts will be useful to many others :)
see you soon!

---

### Post by Icarosaurus on 2007-07-12
Hello, I managed to compile xfoil in single precision, just paying attention on the README.
I'll write a little HOWTO and I hope to get the double precision version to work.
Bye

---

### Post by Icarosaurus on 2007-09-08
Someone made the work for us.
Here is  Xfoil 6.96 in the form of a source package:
[http://www.scientificcomputing.net/debian/packages/xfoil/]("http://www.scientificcomputing.net/debian/packages/xfoil/")
Here is how to install (most of these instructions are taken from the Xfoil mailing list):
1) Install needed pakages (unfortunately, the list is not complete, please post for adding other packages)
```

sudo apt-get install fakeroot g77 debhelper build-essential xorg-dev

```
2) Download all the files there and:
```

dpkg-source -x xfoil_6.96-1.dsc
cd xfoil-6.96
fakeroot debian/rules binary

```
3)Install the package as usual
```
cd ..
sudo dpkg -i  xfoil_6.96-1_i386.deb
```
It's double precision.. thanks to [http://www.scientificcomputing.net]("http://www.scientificcomputing.net") for great work.
You can find other useful scientific software there.
Regards...

---

### Post by Blutack on 2007-11-20
Horrendous!
You also need to have the following packages
g77, debhelper, build-essential, xorg-dev
plus some others I may have forgotten about.

---

### Post by Icarosaurus on 2007-11-21
Why horrendous?
Maybe I had all those package you said installed, and I didn't see they were needed.
Anyway, Xfoil works nice.
I don't accept your easy "horrendous", cause I wrote to give a contribution and help others. Your complains are a nonsense, here.
So, all I can do is listing the packages you mentioned ('cause it's your wellcome genuine contribution) and asking to you to remember the other ones.

---

### Post by Blutack on 2007-12-06
I'm sorry.  I was rather frustrated at the time, and I was trying to work out which of the several fortran compilers ubuntu has I needed.  The horrendous was not at all directed at your howto, without which I wouldn't have had a cat in hells chance.  Many thanks, and apologies again.  I would post my package but there is a size limit on the forum.

---

### Post by Icarosaurus on 2007-12-09
Well, I know sometimes it's frustrating... ;)
I had the best result with Intel fortran compiler and I was able to compile source all  in double precision.
I have to learn how to make deb packages, so maybe I could put them on an ftp account and give you all the link.
I compiled AVL too, so.. stay tuned :)

---

### Post by Icarosaurus on 2007-12-09
Here it is:
[Xfoil 6.96 .deb package]("http://giuschet.altervista.org/Ubuntu/")

Compiled with intel fortran compiler, on an amd athlon machine, all in double precision.
Let me know...

---

### Post by Blutack on 2007-12-11
Awesome!  I would have uploaded mine but the size limit is too low.  You thought about contacting getdeb.net?

---

### Post by Icarosaurus on 2007-12-12
Yes...I thought contacting getdeb.
Actually I'm taking an account. Stay tuned :)

---

### Post by phillip_peters52 on 2008-03-26
I am trying to install Xfoil in Ubuntu Gutsy Gibbon i have follwed the instructions on this thread and in the readme files that come with the files but i cannot build the plot library.

Can anyone help?

---

### Post by Icarosaurus on 2008-03-26
Try downloading my deb package for 32 bit machines [here]("http://giuschet.altervista.org/Ubuntu/").
Let me know...

---

### Post by phillip_peters52 on 2008-03-27
After downloading the deb package and typing in the xfoil command to run i receive this error message

xfoil: error while loading shared libraries: libifport.so.5: cannot open shared object file: No such file or directory

---

### Post by Icarosaurus on 2008-03-28
Thank you for your report.
I have your same problem with Hardy.
The problem is related to an Intel Fortran library... I'll try to fix it as soon as possible.

---

### Post by pritamps on 2008-04-02
Hey,

Even I got the error about the intel fortran compiler, but it worked fine when I installed following the instruction on the first page of the thread (from scientificcomputing) 

Thanks a lot!

---

### Post by phillip_peters52 on 2008-04-03
As i said previously i have tried installing from the directions on the first page and cannot get the plot library to compile. 

Following the advice given I then trid installing from the debian package and got the error messae above.

---

### Post by Icarosaurus on 2008-04-07
I just compiled Xfoil 6.97.
I'll soon release a package. Please be patient
:)

---

### Post by Icarosaurus on 2008-04-07
[Here it is]("http://giuschet.altervista.org/Ubuntu/") 
Let me know... maybe I'll modify the first post, so the link could be more accessible.
Bye :)

---

### Post by pritamps on 2008-04-09
Thanks a lot!

I had got the tar.gz compiled, but was unable to get any graphics (I have no experience with ./configure :) ). this deb file worked perfectly!

---

### Post by Icarosaurus on 2008-04-09
You're wellcome, 
Maybe I'll have to compile again and make a new package, cause bugs were found and corrected.
I've attached the package to the first post.

---

### Post by VTphilipv on 2008-09-12
On a similar note... has anybody hat any luck with installing AVL by Mark Drela on a 64 bit ubuntu?
"Back in the day" I found .deb file that worked like the Xfoil one...

---

### Post by VTphilipv on 2008-10-07
*bump*

---

### Post by Icarosaurus on 2008-10-08
Sorry..I'm a bit busy working on my Thesis :p
I didn't compile avl on a 64 bit ubuntu, but, as far as i remember, I didn't have particular issues compiling on 32 bit following the istructions.

---

### Post by rubisher on 2008-10-27
> **Icarosaurus said:**
> Someone made the work for us.
Here is  Xfoil 6.96 in the form of a source package:
[http://www.scientificcomputing.net/debian/packages/xfoil/]("http://www.scientificcomputing.net/debian/packages/xfoil/")

[snip]


Unfortunately, this link doesn't seems to still answer.
I would also like to rebuild Xfoil but for another platform (ppc64 or parisc: nothing else available).
If ever you could post (or put on your home page) diff and dsc files, it would be of great additional help.

Tia,
    r.

---

### Post by Icarosaurus on 2008-10-27
I'm sorry... I compiled Xfoil from source and i made the package.
I didn't produce any .diff or .src and I can't find the files downloaded from that site.

I know, I should post detailed instructions on how to compile and modifying the Makefile, for helping you all in compiling for different architectures. My fault.

---

### Post by rubisher on 2008-10-28
> **Icarosaurus said:**
> I'm sorry... I compiled Xfoil from source and i made the package.
I didn't produce any .diff or .src and I can't find the files downloaded from that site.

No pb, I was just hopping somebody have a copy somewhere in a corner of its hd ;-)

> **Icarosaurus said:**
> 
I know, I should post detailed instructions on how to compile and modifying the Makefile, for helping you all in compiling for different architectures. My fault.
Don't worry, Gentoo stuff are available around that, it's just hard to me to build a deb pkg???

Thanks again for your kind attention,
r.

---

### Post by Icarosaurus on 2008-10-28
well... building a package is not hard if you have all stuff correctly compiled.

---

### Post by 080801jk on 2008-10-30
2003&#24180; 9&#26376;&#65292;&#32431;&#31929;&#22312;&#19968;&#20010;&#31616;&#21333;&#30340;&#27665;&#23621;&#37324;&#30001;&#19977;&#20154;&#32452;&#24314;&#65292;[**&#23130;&#32433;&#25668;&#24433;**](http://www.chuncui.net/)&#22235;&#24180;&#30340;&#39118;&#39118;&#38632;&#38632;&#19968;&#36335; &#36208;&#26469;&#65292;[**&#19978;&#28023;&#23130;&#32433;&#25668;**&#24433;](http://www.chuncui.net/shhssygzs.htm)&#32463;&#21382;&#21508;&#31181;&#33392;&#38590;&#12290;&#19981;&#26029;&#23457;&#35270;&#21644;&#23436;&#21892;&#33258;&#25105;&#65292;&#25171;&#36896;&#39640;&#31471;&#31169;&#20154;&#25668;&#24433;&#21697;&#29260;&#19968;&#30452;&#26159;&#25105;&#20204;&#30340;&#30446;&#26631;&#12290;[**&#28145;&#22323;&#23130;&#32433;&#25668;&#24433;**](http://www.chuncui.net/szhssygzs.htm)&#19981;&#26029;&#21457;&#23637;&#21644;&#28145;&#21270;&#31649;&#29702;&#65292;&#36804;&#20170;&#20026;&#27490;&#24050;&#21457;&#23637;&#25104;&#20026;&#21271;&#20140;&#65292;&#19978;&#28023;&#65292;&#28145;&#22323;&#19977;&#23478;&#24215;&#65292;[&#22266;&#23450;&#36164;&#20135;200&#22810;&#19975;&#20803;&#65292;[**&#24191;&#24030;&#23130;&#32433;&#25668;&#24433;**](http://www.chuncui.net/gzhssy.htm)&#33829;&#19994;&#38754;&#31215;800&#22810;&#24179;&#21830;&#21153;&#36710;5&#36742;&#65292;&#26071;&#19979;&#21592;40&#22810;&#20154;&#30340;&#25668;&#24433;&#22242;&#38431;&#65292;&#26381;&#21153;&#36807;&#26469;&#33258;&#20840;&#29699;&#21508;&#22320;&#30340;&#26032;&#20154;2000&#22810;&#23545;&#12290;

---

### Post by Icarosaurus on 2008-11-27
For those interested, I wrote a Howto for compiling XFoil [here]("http://ubuntuforums.org/showthread.php?t=994912")

---

### Post by azredwing on 2009-09-14
Got this working for Jaunty x64.

Note that 
> 
dpkg -x xfoil_6.97-1_i386.deb .
sudo cp usr/lib/libg2c* /usr/lib32/
rm -r usr


should have actually read
> 
dpkg -x libg2c0_3.4.6-8ubuntu2_i386.deb .
sudo cp usr/lib/libg2c* /usr/lib32/
rm -r usr


It's been a really long time so I don't expect that this happened, but was a x64 .deb ever developed?

---

### Post by smani on 2009-12-25
Here is Xfoil for amd64, using double precision and the Intel fortran compiler. Tested on Fedora 12 and Ubuntu 9.10.

Download:
[http://n.ethz.ch/~smani/download/xfoil-6.97_amd64_ifort_dbl.tar.gz](http://n.ethz.ch/~smani/download/xfoil-6.97_amd64_ifort_dbl.tar.gz)

---

### Post by pritamps on 2010-01-02
Awesomme!! Thanks!

---

### Post by openae on 2010-01-05
Hey thanks for all your hard work guys (with the tutorials and installation packages)!

I actually started an open aerospace community specializing in stuff like this ([http://openae.org](http://openae.org)). We are currently hosting Icarosaurus's two xfoil DEB packages, along with directions on how to quickly get it running on Karmic.

You can find them all here | [http://openae.org/xfoil-download](http://openae.org/xfoil-download)

If any of you guys have some time, it would be great if you can contribute a couple of article to the community :guitar:

Thanks again for all this wonderful information!

---

### Post by azredwing on 2010-06-09
> **openae said:**
> Hey thanks for all your hard work guys (with the tutorials and installation packages)!

I actually started an open aerospace community specializing in stuff like this ([http://openae.org](http://openae.org)). We are currently hosting Icarosaurus's two xfoil DEB packages, along with directions on how to quickly get it running on Karmic.

You can find them all here | [http://openae.org/xfoil-download](http://openae.org/xfoil-download)

If any of you guys have some time, it would be great if you can contribute a couple of article to the community :guitar:

Thanks again for all this wonderful information!

I realize this is a little late, but thanks for this! I just reinstalled XFOIL for my 64-bit machine and this made it a snap.

---

### Post by dewapur on 2010-07-27
If you are using Lucid, apt-get install xfoil would do. I just knew it yesterday that Lucid comes with package xfoil 6.97. You can check [here]("http://packages.ubuntu.com/en/lucid/xfoil").

---

### Post by azredwing on 2010-08-21
> **dewapur said:**
> If you are using Lucid, apt-get install xfoil would do. I just knew it yesterday that Lucid comes with package xfoil 6.97. You can check [here]("http://packages.ubuntu.com/en/lucid/xfoil").

Nice. Thanks for this.

---

