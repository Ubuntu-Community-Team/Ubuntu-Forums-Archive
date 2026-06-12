---
title: "Sane 1.0.18 (for hp3500 driver)"
date: 2006-08-03
forum: Desktop Environments
---

### Post by toMeloos on 2006-08-03
Ubuntu dapper includes libsane and sane-utils version 1.0.17. The latest stable sane-backend driver is currently 1.0.18, which finally contains the hp3500 driver that I need to get my scanner working.

As I am not used to diverging from the official ubuntu package versions and there do not seem to be debs around of sane 1.0.18, I would like to ask if someone could tell me what would be the best way to install this (keeping in mind dependancies on the packages etc.)?

---

### Post by TiredBird on 2006-08-03
I have exactly the same problem. I am running 6.06 and trying to connect an HP Scanjet 3500c. I have found the what I am looking for is in sane backend 1.0.18 but I have never installed anything except through Synaptic. If I have the right stuff on my system I would be willing to follow directions though.

---

### Post by Orval on 2006-08-04
This is very good news! Finally I can use my HP3570c scanner in Ubuntu! [IMG]http://www.hobbybrouwen.nl/forum/Smileys/default/elifant.gif[/IMG]

But indeed: who will make a deb-file?

---

### Post by Orval on 2006-08-04
Maybe the deb from the Debian site works:

[HERE]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fs%2Fsane-backends%2Flibsane_1.0.18-2_i386.deb&md5sum=a575f52a052ebf0f8488535149beb36c&arch=i386&type=main").

Can't try it now, because I am at work right now.

---

### Post by toMeloos on 2006-08-06
Did some quick searches and those 1.0.18 packages seem to be available and will be included in Edgy Eft:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libsane&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libsane&searchon=names&subword=1&version=all&release=all)

However these have dependancies that cannot be met by dapper. 

Backporting would be the best option. I've submitted a request. You can monitor (and endorse!) it here:

[https://launchpad.net/products/dapper-backports/+bug/55431](https://launchpad.net/products/dapper-backports/+bug/55431)

---

### Post by Orval on 2006-08-07
Well, I downloaded the source, applied the patch, compiled and installed and it worked. However, if I do 

> scanimage -L

it says a HP3500 scanner is found (i actually have a HP3570c), and with scanimage the scanner starts to scan. But XSane and Kooka cannot find a scanner.

Compiling and installing the latest frontends did not help.

---

### Post by toMeloos on 2006-08-16
It seems the backports are kind of unmaintained.... this request and many others have been untriaged for some time. I hope someone of the backporting team starts working on it soon.

---

### Post by geovino on 2007-03-04
How do you install this? Is it in Synaptic? What's the command for the terminal?

---

