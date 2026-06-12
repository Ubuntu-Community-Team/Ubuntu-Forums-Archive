---
title: "Baghira Nightly Tarball Problem"
date: 2005-12-22
forum: General Help
---

### Post by funkyou on 2005-12-22
Well, i tried several times to fetch the latest baghira-style with cvs,
but it took the whole night to fetch just a bit of it...

So i tried the nightly tarball... But it does not compile or works in any way...
There has something strange happened with the files...

Every file from the nightly tarball has a ",v" attached to the filename, look here:
[B]Makefile.am,v
Makefile.cvs,v
INSTALL,v
README,v[/B]

This ",v" is attached to every file in the archive, and when i look into on of these
files, there is some type of header in it, which looks like:
[B]head	1.3;
access;
symbols
	vendor:1.1.1
	start:1.1.1.1
	baghira-style:1.1.1;
locks; strict;
comment	@# @;


1.3
date	2005.07.31.16.15.55;	author baghira-style;	state Exp;
branches;
next	1.2;

1.2
date	2005.05.08.10.48.50;	author baghira-style;	state Exp;
branches;
next	1.1;

1.1
date	2005.03.21.18.02.46;	author baghira-style;	state Exp;
branches
	1.1.1.1;
next	;

1.1.1.1
date	2005.03.21.18.02.46;	author baghira-style;	state Exp;
branches;
next	;


desc
@@


1.3
log
@overall stuff
@
text
@
[/B]

so, how can i build the nightly baghira-tarball??? or exists a cvs-tarball or a
kubuntu breezy package outthere, which is able to be used by me???

thx for any help

---

### Post by Freddy on 2005-12-22
Hi I've been using Baghira CVS for a long time now. I have allways taken it directly from CVS, fast and with no problem.
Just for the hell of it I downloaded the nightly tarball, downloaded kde admin to home/user/baghira/baghira folder and run "make -f Makefile.cvs" but as you said no luck with that. 

The strange thing is that the nightly tarball and the files taken directly from CVS don't look the same, so I suggest you try again with CVS cause it's allways been very fast for me (10 seconds) or you could allways post a question over at their forum, Thomas allways tries to help out, he even fixed some code for me that didn't work that well in Kubuntu.   /// Freddan

---

### Post by Freddy on 2005-12-22
Hi again, if you are having trouble with the CVS, you can download this. It's a new CVS (22/12/05), with the kde admin directory already donloaded, so its just a simple. 
```
make -f Makefile.cvs
./configure --prefix=`kde-config --prefix`
make
sudo make install
```
/// Freddan

---

### Post by funkyou on 2005-12-25
Thanks for your help and happy christmas :)

I have already managed to get cvs working, dont know why,
but it works now... (i have changed nothing, just tried again
and it was fast...)

Indeed, after trying i think baghira is way to buggy for me...

Again, thankyou

---

### Post by Freddy on 2005-12-25
Buggy ? I find Baghira to be very stable, what's your problems with it?   /// Freddan

---

