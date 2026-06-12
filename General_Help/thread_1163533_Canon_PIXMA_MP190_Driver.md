---
title: "Canon PIXMA MP190 Driver?"
date: 2009-05-18
forum: General Help
---

### Post by coldReactive on 2009-05-18
> **AlexanderDGreat said:**
> I'm using Ubuntu 9.04 64 bit.

For 32 & 64 bit users: Use Ubuntu MP180 driver, but scanning won't work, (wbee are you using 32 or 64 bit? How did you make the scanner work?) You can also download driver (MP 190) from Canon Website, I assume this will make print and scan work, but it's only for 32 bit. What's left for us 64 bit users is to find a useful driver and make scanning work. The solution is to compile from source (as lykwydchykyn suggested). Will this effort really make printing and scanning work for 64 bit? I'm going to try this path.

Do this (tested for karmic only, doesn't work on Hardy):

0. TURN OFF THE PIXMA MP190 (Mandatory)

1. Remove the printer you currently have in the printers that uses the MP180 driver.

2. Install this: [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.1_all.deb)

3. Download the canon-europe i386 drivers from: [http://software.canon-europe.com/software/0031326.asp?model=](http://software.canon-europe.com/software/0031326.asp?model=)

4. Force architecture on all four DEBs using the following command:
```
sudo dpkg -i --force-architecture <deb_package>
```

5. Turn on the printer/scanner. Ubuntu will auto-detect your printer as MP190-series.

---

### Post by coldReactive on 2009-05-21
I guess this is just a shot in the dark?

---

### Post by chriskin on 2009-05-21
why open it in windows?
you can open your tar archive inside linux
it is just that the windows app cannot open tars, most probably

---

### Post by chriskin on 2009-05-21
also, having a printer of the same company, when i tried to add it at system/administration/printing it downloaded all the drivers automatically and it works just fine (worked at least, i no longer use it in favor of my new HP printer :) )

have you tried that before going to a site?

if you do need a driver from a site, it would better to get a .deb if it available, rpm packages can be installed on debian based systems like ubuntu, but they need extra work, while debs just need two clicks

---

### Post by coldReactive on 2009-05-21
There are no debs for it available.

[http://www.google.com/#hl=en&ei=yVAVSsKlPJSS9QSEspDHAg&sa=X&oi=spell&resnum=1&ct=result&cd=1&q=PIXMA+MP+190+deb+driver&spell=1&fp=Li-R6mbKWrc](http://www.google.com/#hl=en&ei=yVAVSsKlPJSS9QSEspDHAg&sa=X&oi=spell&resnum=1&ct=result&cd=1&q=PIXMA+MP+190+deb+driver&spell=1&fp=Li-R6mbKWrc)

---

### Post by chriskin on 2009-05-21
you didn't answer if you managed to open the archive in ubuntu, or if you did what i said with the driver, those where the important part of my messages :)

---

### Post by coldReactive on 2009-05-21
> **chriskin said:**
> you didn't answer if you managed to open the archive in ubuntu, or if you did what i said with the driver, those where the important part of my messages :)

Currently, I do not have Ubuntu installed, I was hoping someone could confirm the contents of the TAR to be an RPM file so I can reinstall ubuntu and install alien.

---

### Post by chriskin on 2009-05-21
o ok, let me get it for you one moment and i will tell you

---

### Post by chriskin on 2009-05-21
so, there are two tars inside the tar, each one having two rpms and a tar inside of them

the first one is the drivers for the printer and the second one for the scanner, or so it seems

---

### Post by coldReactive on 2009-05-21
Thanks a lot, now to wait about half an hour to install Ubuntu. ;)

---

### Post by coldReactive on 2009-05-21
Okay, so I got into ubuntu finally, and tried to convert the RPMs to debs, but...

```
ian@ian-desktop:~/Desktop/RARs$ sudo alien --to-deb cnijfilter-common-3.00-1.i386.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/cnijfilter-common
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: failure: couldn't find library libpopt.so.0 needed by debian/cnijfilter-common/usr/lib/cups/filter/pstocanonij (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: `cnijfilter-common-3.00': No such file or directory
```

Also, here's an image from the printer drivers section:

[img]http://i39.tinypic.com/w8th0g.png[/img]

---

### Post by coldReactive on 2009-05-21
And when I tried using RPM to install it directly:

```
ian@ian-desktop:~/Desktop/RARs$ sudo rpm -i cnijfilter-common-3.00-1.i386.rpmerror: Failed dependencies:
	/bin/sh is needed by cnijfilter-common-3.00-1.i386
	cups is needed by cnijfilter-common-3.00-1.i386
	libc.so.6 is needed by cnijfilter-common-3.00-1.i386
	libc.so.6(GLIBC_2.0) is needed by cnijfilter-common-3.00-1.i386
	libc.so.6(GLIBC_2.1) is needed by cnijfilter-common-3.00-1.i386
	libc.so.6(GLIBC_2.3) is needed by cnijfilter-common-3.00-1.i386
	libcups.so.2 is needed by cnijfilter-common-3.00-1.i386
	libpopt.so.0 is needed by cnijfilter-common-3.00-1.i386
	popt is needed by cnijfilter-common-3.00-1.i386
ian@ian-desktop:~/Desktop/RARs$ sudo apt-get install cups
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cups is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by chriskin on 2009-05-21
alien has always worked for me, so i can't say anything productive from now on, let's hope that someone had the same problem and fixed it 


i just have a question, besides the rpm there is a tar as well, what does it have inside it?

---

### Post by coldReactive on 2009-05-21
> **chriskin said:**
> alien has always worked for me, so i can't say anything productive from now on, let's hope that someone had the same problem and fixed it 


i just have a question, besides the rpm there is a tar as well, what does it have inside it?

Even if there were things inside of it, they're probably just source versions of their RPMs. I didn't look into them because I never like or care to make from source.

Back to windows for me.

---

### Post by chriskin on 2009-05-21
> **coldReactive said:**
> Even if there were things inside of it, they're probably just source versions of their RPMs. I didn't look into them because I never like or care to make from source.

Back to windows for me.

if it is source, it would be like 3 commands and over
most probably
./configure
make
make install

or even better, just a script
if you choose to solve your problem that way, i can , most probably, help

(if , of course, you don't really want to solve your problem , that's none of my concern - it's just so easy solving things in the terminal that i do not see the reason why)

---

### Post by lykwydchykyn on 2009-05-21
Don't know if you've seen this site:
[http://mp610.blogspot.com/](http://mp610.blogspot.com/)

I got my mp620 working (scanning and printing) with Linux using the instructions I found there.

Looks like part of the problem is that you're running 64 bit Ubuntu.  I've not had much luck with alien on 64 bit, though I know there's some kung-fu you can do that will make it work.

Since you're on a fresh install anyway, why not try it with 32 bit Ubuntu?

---

### Post by toychina on 2009-06-06
Hi,
I've found some .deb drivers on the canon-europe website : [http://software.canon-europe.com/products/0010639.asp](http://software.canon-europe.com/products/0010639.asp)

Just select the OS on the top.

bye

---

### Post by d0b33 on 2009-06-08
> **toychina said:**
> Hi,
I've found some .deb drivers on the canon-europe website : [http://software.canon-europe.com/products/0010639.asp](http://software.canon-europe.com/products/0010639.asp)

Just select the OS on the top.

bye

Thanks!

Edit:
darn not 64bit, I need help for 64bit... I bought this printer because a newegg reviewer said it works on ubuntu he probably meant 32bit.

Edit2:
Got it working, have to use the mp180 drivers of ubuntu using the ubuntu printer wizard.

---

### Post by coldReactive on 2009-06-09
> **d0b33 said:**
> Edit2:
Got it working, have to use the mp180 drivers of ubuntu using the ubuntu printer wizard.

But what about the scanner portion?

---

### Post by d0b33 on 2009-06-09
> **coldReactive said:**
> But what about the scanner portion?

Ya still no luck with that, I use virtualbox to scan running xP for now, works flawlessly.

I installed the canon drivers on 64bit ubuntu using the -force extension and the printer driver works but not scanner.

---

### Post by lykwydchykyn on 2009-06-09
Scanning support should be working in the very latest release of sane-backends, which has just been released.  It's not in Ubuntu, but it is in Debian sid so you can compile from Debian sources if you're so inclined. (I did this and it's working for me).

If not, I'd expect karmic koala to include the latest sane-backends so canon support should be much improved by october.

---

### Post by coldReactive on 2009-06-11
> **lykwydchykyn said:**
> Scanning support should be working in the very latest release of sane-backends, which has just been released.  It's not in Ubuntu, but it is in Debian sid so you can compile from Debian sources if you're so inclined. (I did this and it's working for me).

If not, I'd expect karmic koala to include the latest sane-backends so canon support should be much improved by october.

And how do I compile from debian in the way you mentioned in Ubuntu?

---

### Post by wbee on 2009-06-11
Hello,

I also have a Canon Pixma190. I picked it up at Wal-Mart on impulse,because it was the printer/scanner,the USB cable,two starter inks,and a pack of photo paper for thirty dollars. It is a perfectly acceptable printer/scanner for casual use.

My *GUESS* is it is a Canon Pixma180 with a new number,to designate the one with the aforementioned accessories.

That said,following the directions a page back,I loaded the "cups" driver for the 180 and it worked perfectly---including the scanner function.

Good luck,

-----------

W

---

### Post by coldReactive on 2009-06-11
> **wbee said:**
> Hello,

I also have a Canon Pixma190. I picked it up at Wal-Mart on impulse,because it was the printer/scanner,the USB cable,two starter inks,and a pack of photo paper for thirty dollars. It is a perfectly acceptable printer/scanner for casual use.

My *GUESS* is it is a Canon Pixma180 with a new number,to designate the one with the aforementioned accessories.

That said,following the directions a page back,I loaded the "cups" driver for the 180 and it worked perfectly---including the scanner function.

Good luck,

-----------

W

You mean this driver?

[img]http://i39.tinypic.com/w8th0g.png[/img]

---

### Post by lykwydchykyn on 2009-06-11
> **coldReactive said:**
> And how do I compile from debian in the way you mentioned in Ubuntu?

First, get the sourcecode here:
[http://ftp.de.debian.org/debian/pool/main/s/sane-backends/sane-backends_1.0.20.orig.tar.gz](http://ftp.de.debian.org/debian/pool/main/s/sane-backends/sane-backends_1.0.20.orig.tar.gz)

Then read this:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

I haven't done this in Ubuntu, just debian, but since we're compiling from source it should work in any Linux.

---

### Post by wbee on 2009-06-12
coldReactive,

Yes,exactly.

---

### Post by coldReactive on 2009-06-12
> **wbee said:**
> coldReactive,

Yes,exactly.

Was hoping the scanner function would work for me like it did you, but Xsane said there were no scanning devices, sadly.

I don't want to make from source, so I'll wait for Karmic. If Karmic doesn't have it, I'll have to wait for the next one, and if that one (the LTS) doesn't have it, goodbye Ubuntu. Because ReactOS should be much more stable by then.

---

### Post by lykwydchykyn on 2009-06-12
> **coldReactive said:**
> Was hoping the scanner function would work for me like it did you, but Xsane said there were no scanning devices, sadly.

I don't want to make from source, so I'll wait for Karmic. If Karmic doesn't have it, I'll have to wait for the next one, and if that one (the LTS) doesn't have it, goodbye Ubuntu. Because ReactOS should be much more stable by then.

[http://packages.ubuntu.com/en/source/karmic/sane-backends](http://packages.ubuntu.com/en/source/karmic/sane-backends)

The new version will be in Karmic.

---

### Post by wbee on 2009-06-12
Cold Reactive:

Something I should have mentioned but did not,and this is so weird it goes over my head,but perhaps someone else will see this and get it.

Xsane SAYS it recognizes my tv tuner card as the scanner,but when I try it by putting something in and hitting "scan",it works.

This is free advice and possibly well worth it.:-)

I would follow lykwydchykyn's advise and install it that way.

Beyond that,I hesitate to say more,not wanting to do more harm than good.

I hope you resolve this.

---

### Post by d0b33 on 2009-06-18
> **wbee said:**
> Cold Reactive:

Something I should have mentioned but did not,and this is so weird it goes over my head,but perhaps someone else will see this and get it.

Xsane SAYS it recognizes my tv tuner card as the scanner,but when I try it by putting something in and hitting "scan",it works.


ya, my hauppauge tuner gets in the way too.

---

### Post by Aquahop on 2009-07-09
> **lykwydchykyn said:**
> First, get the sourcecode here:
[http://ftp.de.debian.org/debian/pool/main/s/sane-backends/sane-backends_1.0.20.orig.tar.gz](http://ftp.de.debian.org/debian/pool/main/s/sane-backends/sane-backends_1.0.20.orig.tar.gz)

Then read this:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

I haven't done this in Ubuntu, just debian, but since we're compiling from source it should work in any Linux.


This worked great on my system, in a snap.  I tried other suggestions, but none worked until I found your suggestion.  It's tough sorting out all the bull!

Thanks,
Chuck
Ubuntu-Hardy Heron;)

---

### Post by milky2313 on 2009-07-31
Just got this printer today and I am quite happy with it. As with coldReactive, the print function works great for me using the MP180 driver already included in Ubuntu 9.04.  As for scanning, Xsane and flegita still do not recognize the scanner.  However, (as a previous poster mentioned) the Cannon European website does have .deb driver packages for the printer and scanner functions.

Install the 2 scangear packages and then type "scangearmp" in a terminal to start the simple scanning utility that works great (at least for me).  This should work good at least until xsane starts supporting this device. (I have not tested cannon's printer driver packages yet, only the scangear part)

Here is the link again for the .deb driver packages from Cannon 
[http://software.canon-europe.com/products/0010639.asp]("http://software.canon-europe.com/products/0010639.asp")

Hope this helps...

---

### Post by coldReactive on 2009-07-31
DEB packages are most likely for x86, and not x64 (which is what I use). Ubuntu won't install a deb package that's x86 in x64.

---

### Post by AlexanderDGreat on 2009-11-12
I'm using Ubuntu 9.04 64 bit.

For 32 & 64 bit users: Use Ubuntu MP180 driver, but scanning won't work, (wbee are you using 32 or 64 bit? How did you make the scanner work?) You can also download driver (MP 190) from Canon Website, I assume this will make print and scan work, but it's only for 32 bit. What's left for us 64 bit users is to find a useful driver and make scanning work. The solution is to compile from source (as lykwydchykyn suggested). Will this effort really make printing and scanning work for 64 bit? I'm going to try this path.

---

### Post by coldReactive on 2009-11-12
> **AlexanderDGreat said:**
> I'm using Ubuntu 9.04 64 bit.

For 32 & 64 bit users: Use Ubuntu MP180 driver, but scanning won't work, (wbee are you using 32 or 64 bit? How did you make the scanner work?) You can also download driver (MP 190) from Canon Website, I assume this will make print and scan work, but it's only for 32 bit. What's left for us 64 bit users is to find a useful driver and make scanning work. The solution is to compile from source (as lykwydchykyn suggested). Will this effort really make printing and scanning work for 64 bit? I'm going to try this path.

Do this (tested for karmic only, doesn't work on Hardy):

0. TURN OFF THE PIXMA MP190 (Mandatory)

1. Remove the printer you currently have in the printers that uses the MP180 driver.

2. Install this: [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.1_all.deb)

3. Download the canon-europe i386 drivers from: [http://software.canon-europe.com/software/0031326.asp?model=](http://software.canon-europe.com/software/0031326.asp?model=)

4. Force architecture on all four DEBs using the following command:
```
sudo dpkg -i --force-architecture <deb_package>
```

5. Turn on the printer/scanner. Ubuntu will auto-detect your printer as MP190-series.

---

### Post by AlexanderDGreat on 2009-11-12
Hi coldReactive thanks for the info, but how about JJ? Will this work? I can't upgrade to Karmic just yet, no time.

PS Your #2 link is not working.

PPS You're saying that after doing steps above, scanning and printing will work?

PPPS This is for 64 bit because you said --force-architecture right?

---

### Post by coldReactive on 2009-11-12
> **AlexanderDGreat said:**
> Hi coldReactive thanks for the info, but how about JJ? Will this work? I can't upgrade to Karmic just yet, no time.

PS Your #2 link is not working.

PPS You're saying that after doing steps above, scanning and printing will work?

PPPS This is for 64 bit because you said --force-architecture right?

This is for 64-bit, yes.

Get the drivers here: [http://files.canon-europe.com/files/soft31326/software/MP190_debian_drivers.tar](http://files.canon-europe.com/files/soft31326/software/MP190_debian_drivers.tar)

if that doesn't work, you'll have to manually navigate the canon-europe site yourself.

---

### Post by AlexanderDGreat on 2009-11-15
Great. Thanks for sharing.

---

### Post by allanvaliati on 2010-07-30
Possible problem after installing mp190 drivers:

-cant scan:
Try this on terminal: **scangearmp**

Make sure that the printer is on and connected to pc.
In ubuntu 10.04 scanning was natively supported, but on jolicloud it still is not. 



- cant change printing options
Try: **cngpij**

---

### Post by allanvaliati on 2010-07-30
[[IMG]http://img695.imageshack.us/img695/9946/canony.png[/IMG]](http://img695.imageshack.us/i/canony.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

[[IMG]http://img687.imageshack.us/img687/169/canon2l.th.png[/IMG]](http://img687.imageshack.us/i/canon2l.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by Nemo_bis on 2010-11-23
Now with Ubuntu 10.10 Maverick Merkaat installing mp190 printer and scanner is very easy with debs, see [http://ubuntuforums.org/showpost.php?p=10152751&postcount=9](http://ubuntuforums.org/showpost.php?p=10152751&postcount=9) .

---

