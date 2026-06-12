---
title: "imagemagick problems"
date: 2005-12-07
forum: General Help
---

### Post by coolclassic on 2005-12-07
Synaptic shows imagemagick is installed but no execute file is found. I have used locate and find to find this file but it is not found.Locate finds only the document files and dpkg files, no other file is showen.
 I have also tried to uninstall but it wants to remove "kong-plugins,kdeaddons and kubintu-desktop". As I would rather use this package how do I get it to work?

I have also tried apt-get install with the same result.

---

### Post by Zaventh on 2005-12-07
imagemagick is not a gui imaging editing tool. Instead, it is a collection of binary tools which provide certain functionalities of image manipulation. However, the imagemagick tools are almost always used with third party gui frontends.

If you want to use the tools from the command-line, below is the binary contents of imagemagick:

 /usr/bin/animate
 /usr/bin/compare
 /usr/bin/composite
 /usr/bin/conjure
 /usr/bin/convert
 /usr/bin/display
 /usr/bin/identify
 /usr/bin/import
 /usr/bin/mogrify
 /usr/bin/montage

Here is a list of some of the frontends: [http://www.imagemagick.org/script/api.php](http://www.imagemagick.org/script/api.php)

All this information is directly available from the website...

---

### Post by coolclassic on 2005-12-07
I have used imagemagic with a gui for years infact in hoary it installed using synaptic with full gui.

---

### Post by Zaventh on 2005-12-07
Well, I'm just reading straight from the package description. Open Adept and search for imagemagick to see the possible x frontends you can install. Krita, installed in Breezy by default, uses the imagemagick tool suite.

And by the way, each of those tools can run in an x window interactively.

---

### Post by coolclassic on 2005-12-07
OOPS!!!!

Sorry your right the package I was looking for was kuickshow. I was to enthusastic in reinstalling packages after upgrading that I never check the package names I was familar with.

---

