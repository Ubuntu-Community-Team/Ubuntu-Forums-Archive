---
title: "Installing &quot;The Mana World&quot;"
date: 2005-04-07
forum: Gaming &amp; Leisure
---

### Post by Dko on 2005-04-07
Could someone please help this newb install this game? Ive downloaded the source for it and im kinda of confused on how to do everything to get it to install. LIke these libarys it says it needs in the instructions.  Thanks in advance for any help.

---

### Post by Bjørn on 2005-04-10
Hello, I'm one of the developers, I found this message on Google. :-)

First off, for Ubuntu as a Debian based distribution, there is no need to build The Mana World from source. We provide a .deb package and there is also a .deb package for the most rare library we use (we hope it'll become used more often), Guichan. The latter is unfortunately a bit hidden at the moment until they release it on their website.

Here are the links to the .deb files. The rest is included in Hoary+universe and can be installed through Synaptic. They are libsdl, libsdl_mixer, libsdl_image, libphysfs and libxml2.

[http://themanaworld.org/files/libguichan_0.3.0_i386.deb](http://themanaworld.org/files/libguichan_0.3.0_i386.deb)
[http://prdownloads.sourceforge.net/themanaworld/tmw_0.0.11.2_i386.deb?download](http://prdownloads.sourceforge.net/themanaworld/tmw_0.0.11.2_i386.deb?download)

Recently we've also set up a Debian repository that you can probably use with Ubuntu as well, see our download page for details. This could make it easier to update when we release a new version.

As for actually building from source, would you still want to do that. Then you'll need to install the development versions of the above libraries as well, except our libguichan package includes also development files. If you have more questions about this feel free to ask when you have problems.

---

### Post by kamstrup on 2005-05-18
The libguichan link seems to be dead :-S ??

---

### Post by Bjørn on 2005-05-18
Yes the links are now outdated, note I posted them over a month ago. :-)

We've released version 0.0.12 of TMW earlier this month, and I think the best way to install it now is to add our Debian repository which will make sure libguichan can be installed as well. See our download page at [http://themanaworld.org/](http://themanaworld.org/) for details. If you would still prefer to download the files directly, here are the direct links:

[http://prdownloads.sourceforge.net/themanaworld/tmw_0.0.12-1_i386.deb?download](http://prdownloads.sourceforge.net/themanaworld/tmw_0.0.12-1_i386.deb?download)
[http://themanaworld.org/files/debrepo/libguichan_0.3.0-1_i386.deb](http://themanaworld.org/files/debrepo/libguichan_0.3.0-1_i386.deb)

Guichan 0.4.0 was released today but I don't think TMW 0.0.12 will work with it as at the moment Guichan is too much in development to offer binary compatibility. Source combatibility could be there, but isn't guaranteed either. At least start of June there will be TMW 0.0.13 which will use Guichan 0.4.0.

---

### Post by Arktis on 2005-08-28
Whoops, didn't notice where I was posting (just clicked on a search result) This area is for warty, not hoary, which is what I was posting about.  My bad.

---

### Post by plumcreek on 2005-09-30
I'm in the wrong place too.

oops

---

