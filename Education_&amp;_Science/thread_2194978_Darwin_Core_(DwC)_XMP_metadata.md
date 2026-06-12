---
title: "Darwin Core (DwC) XMP metadata"
date: 2013-12-21
forum: Education &amp; Science
---

### Post by alan-pater on 2013-12-21
Hi all

After spending a month in the Ecuadorian Amazon and working with Diego on his camera trap project, ( [https://www.facebook.com/pages/Tiputini/27400169892](https://www.facebook.com/pages/Tiputini/27400169892) ) I decided to work on getting Darwin Core (DwC) supported in free software. DwC allows researchers to add relevant metadata to images and other files. More info on DwC is here: [http://rs.tdwg.org/dwc/terms/](http://rs.tdwg.org/dwc/terms/)

So far, I have found that exiftool has full read/write support to DwC metadata: [http://u88.n24.queensu.ca/exiftool/forum/index.php/topic,4442.0/all.html](http://u88.n24.queensu.ca/exiftool/forum/index.php/topic,4442.0/all.html)
Thanks to Frank & Phil for doing the work to make that happen! However, most Ubuntu versions have an old version of exiftool. I found that the deb package from 14.04 installs without issues on previous versions of Ubuntu, so all we need is to get it backported: [https://bugs.launchpad.net/precise-backports/+bug/1259375](https://bugs.launchpad.net/precise-backports/+bug/1259375) 

Many free software projects use the exiv2 library, which currently does not support DwC. But I have slapped together a patch for that and will see if it worksif my poor computer can finish compliing it: [http://dev.exiv2.org/issues/937](http://dev.exiv2.org/issues/937)
If that works, I hope to have support for Dwc in a bunch of projects such as digiKam, shotwell, gimp, gwenview, etc, etc.

I am also working on a pluging for ResourceSpace, a web-based Digital Asset managment application. And I am hoping to build on the work of Mathais Tobler's Camera Base, an MS Access application that does cool stuff with camera trap images.

I have bugs open on various applications that do nasty things to DwC metadata. If anyone here has any ideas on what else can be done to get this fully supported in free software, and to get biologists and students working int the field using free software tools, please post your comments and suggestions.

PS: I have attached a sample image with DwC metadata, and started a ppa for any tools and apps that I can slap together: [https://launchpad.net/~alan-pater/+archive/dwc]("https://launchpad.net/%7Ealan-pater/+archive/dwc")
Anyone is welcome to give me a hand putting together packages!

---

