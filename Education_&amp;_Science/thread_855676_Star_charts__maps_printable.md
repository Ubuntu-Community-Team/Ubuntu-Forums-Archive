---
title: "Star charts / maps printable"
date: 2008-07-10
forum: Education &amp; Science
---

### Post by g_rus on 2008-07-10
I'm looking software to can print star charts. I use gstar, but that is only for the constellations, i need a starchart for students.

I know PP3 [http://pp3.sourceforge.net/](http://pp3.sourceforge.net/) but is some dificult to use, Starchart [http://starchart.sourceforge.net/](http://starchart.sourceforge.net/) is not the quality that i look. I look something like Sky for Win, Kstars don't have support for printeable charts, is a very poor quality.

---

### Post by Friqenstein on 2008-07-14
Unfortunately, I still use a few winbloz applications for alot of my astronomy activities.
However, you could try Cartes du Ciel.

You can find it at:
[[COLOR="DarkOrange"]http://www.stargazing.net/astropc/[/COLOR]]("http://www.stargazing.net/astropc/")

And yes there is a Linux version available.  :)

---

### Post by g_rus on 2008-07-17
Yes, i know a Cartes du Ciel, is a veru good program.

Well, i saw news poscripts (no jpeg) examples of starcharts and perhaps is the software that i look, have a very good quiality. But i have probles at install, i don't understand how install starcharts and starpng and starpost. 

On starchart at do ./configure i get this
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gawk... (cached) gawk
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... (cached) yes
checking for compress in -lz... (cached) yes
checking for png_info_init in -lpng... (cached) no
checking for gdImageColorResolve in -lgd... (cached) no
configure: warning: You will need gd
installed to compile starpng.
checking for sin in -lm... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for X... (cached) libraries , headers
checking for ANSI C header files... (cached) yes
checking for strings.h... (cached) yes
checking for sys/time.h... (cached) yes
checking whether time.h and sys/time.h may both be included... (cached) yes
checking for gettimeofday... (cached) yes
creating ./config.status
creating Makefile

Good, ok?
At make, i get this:
gcc  -g -O2  -o starpng  starmain.o parse_input.o readfile.o starm2.o starsupp.o starcust.o starpng.o  -lm -lz
starpng.o: In function `D_color':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:850: undefined reference to `gdImageColorResolve'
starpng.o: In function `D_areafill':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:702: undefined reference to `gdImageFilledPolygon'
starpng.o: In function `D_draw':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:610: undefined reference to `gdImageLine'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:639: undefined reference to `gdImageSetStyle'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:644: undefined reference to `gdImageLine'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:631: undefined reference to `gdImageSetStyle'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:635: undefined reference to `gdImageSetStyle'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:606: undefined reference to `gdImageLine'
starpng.o: In function `drawOther':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1454: undefined reference to `gdImageArc'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1455: undefined reference to `gdImageFillToBorder'
starpng.o: In function `drawUnknown':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1420: undefined reference to `gdImageArc'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1421: undefined reference to `gdImageFillToBorder'
starpng.o: In function `drawClus':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1387: undefined reference to `gdImageArc'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1388: undefined reference to `gdImageFillToBorder'
starpng.o: In function `drawNebu':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1352: undefined reference to `gdImageArc'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1353: undefined reference to `gdImageFillToBorder'
starpng.o: In function `drawGalx':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1316: undefined reference to `gdImageArc'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1317: undefined reference to `gdImageFillToBorder'
starpng.o: In function `drawPlan':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1262: undefined reference to `gdImageArc'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1263: undefined reference to `gdImageFillToBorder'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1256: undefined reference to `gdImageCreateFromPng'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1258: undefined reference to `gdImageCopy'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1259: undefined reference to `gdImageDestroy'
starpng.o: In function `drawStar':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1188: undefined reference to `gdImageArc'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:1189: undefined reference to `gdImageFillToBorder'
starpng.o: In function `D_text':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:958: undefined reference to `gdFontGiant'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:986: undefined reference to `gdImageString'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:959: undefined reference to `gdFontLarge'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:961: undefined reference to `gdFontSmall'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:960: undefined reference to `gdFontMediumBold'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:962: undefined reference to `gdFontTiny'
starpng.o: In function `D_close':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:510: undefined reference to `gdImagePng'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:516: undefined reference to `gdImageDestroy'
starpng.o: In function `D_open':
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:443: undefined reference to `gdImageCreate'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:447: undefined reference to `gdImageColorAllocate'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:448: undefined reference to `gdImageColorAllocate'
/home/fonzy/downloads/starchart-3.2.2+png0.2/starpng.c:451: undefined reference to `gdImageColorAllocate'
collect2: ld devolvió el estado de salida 1
make: *** [starpng] Error 1

not ok. I'm not understand why?
and starpng is not in the tar.gz, is in starpng file that is necesary to download separely, where say BINARIES.

Anyone know how install this?

---

### Post by 080729jk on 2008-10-30
&#23458;&#25143;&#20026;&#20160;&#20040;&#36873;&#25321;&#32593;&#31449;&#25512;&#24191;&#36719;&#20214;[**google&#25490;&#21517;**](http://www.jingke.org/)&#25454;&#36164;&#26009;&#35843;&#26597;&#26174;&#31034;:&#22269;&#22806;&#23458;&#25143;&#22312;&#23547;&#25214;&#36152;&#26131;&#21512;&#20316;&#20249;&#20276;&#30340;&#26041;&#24335;&#19978;&#65292;[**google&#25490;&#21517;**](http://www.jingke.org/)&#20351;&#29992;&#26368;&#22810;&#30340;&#26159;&#25628;&#32034;&#24341;&#25806;&#12290;&#32780;Google&#26159;&#30446;&#21069;&#19990;&#30028;&#33539;&#22260;&#20869;&#26368;&#21463;[**google&#25490;&#21517;**](http://www.jingke.org/)&#27426;&#36814;&#22522;&#20110;&#20840;&#25991;&#26816;&#32034;&#30340;&#25628;&#32034;&#24341;&#25806;&#65292;&#27599;&#22825;&#22788;&#29702;&#30340;&#25628;&#32034;&#35831;&#27714;&#39640;&#36798;2.0&#20159;&#27425;&#65281;&#24182;&#19988;&#20026;Yahoo!&#12289;AOL&#31561;&#19990;&#30028;&#33879;&#21517;&#30340;&#38376;&#25143;&#25552;&#20379;&#21518;&#21488;&#25628;&#32034;&#26381;&#21153;&#12290;[**google&#25490;&#21517;**](http://www.jingke.org/)&#22269;&#22806;&#30693;&#21517;&#25628;&#32034;&#24341;&#25806;&#26377;aol(&#32654;&#22269;&#22312;&#32447;)&#12289;infoseek&#12289;netscape&#12289;exite&#65292;[**google&#25490;&#21517;**](http://www.jingke.org/)&#23427;&#20204;&#30340;&#25628;&#32034;&#32467;&#26524;&#20063;&#26159;&#24341;&#29992;google&#30340;&#65292;&#21482;&#35201;&#20570;&#20102;google&#24038;&#20391;&#25490;&#21517;&#65292;&#22312;&#36825;&#20123;&#25628;&#32034;&#24341;&#25806;&#19978;&#37117;&#26377;&#21516;&#26679;&#38752;&#21069;

---

