---
title: "Can't install ATI drivers"
date: 2007-04-18
forum: Desktop Environments
---

### Post by Makaze on 2007-04-18
I am unable to follow the manual ati driver install directions, as I was instructed to do, since the easy install instructions from [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Installation") didn't work.  I was advised to try the manual install as doing the easy install last time worked for a while but ended in me not being able to boot at all showing a video driver error.

The problem I'm having with the manual install is that I cannot make a .deb from the .run file downloaded in the link for some reason (in the manual install instructions). Here is the error I get:

Code:

```
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
./packages/Ubuntu/ati-packager.sh: 178: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.fY5816
```

---

### Post by aberry5555 on 2007-04-18
are you running something other than an x86 architecture PC? i.e. are you using a macintosh or something similar?

---

### Post by Makaze on 2007-04-18
No, I'm running a Acer Travel-Mate 6460-6752 laptop with a dual boot of Windows XP Pro SP2

---

### Post by Makaze on 2007-04-18
bump

---

### Post by beerorkid on 2007-04-19
wow that way looks difficult.  What would be the advantage?

anyway the best way I have found to install ati or nvidia drivers is with the [envy script.]("http://albertomilone.com/nvidia_scripts1.html")

has never failed me.

---

### Post by aberry5555 on 2007-04-19
The only thing I can think of is that the package isn't designed for dual core or something, I don't think it should have had an effect but usually "architecture" means the layout of your processor. The only think I can suggest is to put the .run on a USB pen, load the live-cd on another PC and try and make a new install that way.

It could, however, be a dodgy download, try downloading it again or downloading a previous version, if there's one there.

Sorry I couldn't be any more help

Good luck!

---

