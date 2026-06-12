---
title: "xjig_2.5-2_i386.deb will install but not its manager"
date: 2013-04-27
forum: Gaming &amp; Leisure
---

### Post by pdlethbridge on 2013-04-27
This install problem has been in all the betas, 

and in ubuntu gnom and U12.10.  lTS fine in U 12.04 LTS.The manage says its missing dependencys I have used this program for years but its only recently that I'v had this proble

---

### Post by Perfect Storm on 2013-04-28
Which dependencies are missing?
You could try install the missing ones manually through [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by pdlethbridge on 2013-05-03
I tryed a few of thos sugestions but I couldnt find the right on I just did a fesash instal of xubuntu vtoday and had the same prpblem but it didnt mention what I was missing. In software center there was an other jigsaw program that had the same depency problem but it gave more clues as to what was causing the problem such as prgrames that were conflicting with one another

---

### Post by pdlethbridge on 2013-05-04
I got the manager to installl in xubuntu, It may have been a bad software upgrade on my part. I will try this on the others as well

---

### Post by webmayo on 2013-05-19
The answer is as follows..
xjigmanager was written in Gambas2. This is no longer support by Ubuntu 13.04

I was unable to transfer the original xjigmanager to Gambas3.

Gambas was never my first choice of a programming language anyway, so I have rewritten the launcher in C++. It is now called 'xJigsaw'

The new launcher is working and is available for download.
xjig will not run unless libjpeg62 is installed. 
(sudo apt-get install libjpeg62)

The launcher will run on ubuntu 12.04, 12.10 and 13.04.
It is available as a deb file for installing, or can be run without installing ( available as a zip file)

xjig is included in 'xJigsaw' and does not need a separate installation.

Les Hardy

---

