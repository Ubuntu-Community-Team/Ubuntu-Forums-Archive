---
title: "Distorted fonts"
date: 2011-07-12
forum: Desktop Environments
---

### Post by puetti on 2011-07-12
Hi all!

Certain applications on my Ubuntu 11.04 machine have very ugly and partially even completely distorted fonts in their menus. An example is the text editor nedit. See attached screenshot...

I have already installed a whole bunch of fonts, but that didn't help. Any ideas what could fix this issue?

Thanks!
Andreas

---

### Post by Frogs Hair on 2011-07-12
Open Appearance Preferences > Fonts and see if any of the rendering options make a difference .

---

### Post by puetti on 2011-07-12
no, that has no effect at all. it was set to "Subpixel smoothing" which I think is ok

---

### Post by Frogs Hair on 2011-07-12
> **puetti said:**
> no, that has no effect at all. it was set to "Subpixel smoothing" which I think is ok

I don't know why only certain applications would be affected :confused:  You may have tried , but see if changing the theme make a difference.

---

### Post by puetti on 2011-07-12
OK, to make it more specific:

I first noticed the problem when I was remotely (via ssh) using programs on other Linux machines (mostly SUSE). But actually I have the same problem on my own machine too. I am attaching another screenshot of my firefox menu. That is all perfect. Ubuntu theme, anti-aliased fonts. However *some* programs (e.g. nedit) show these weird fonts. Could it be an issue with RedHat fonts or so?

---

### Post by Frogs Hair on 2011-07-12
> **puetti said:**
> OK, to make it more specific:

I first noticed the problem when I was remotely (via ssh) using programs on other Linux machines (mostly SUSE). But actually I have the same problem on my own machine too. I am attaching another screenshot of my firefox menu. That is all perfect. Ubuntu theme, anti-aliased fonts. However *some* programs (e.g. nedit) show these weird fonts. Could it be an issue with RedHat fonts or so?

I was thinking about the font packages earlier , but it is not clear why only certain applications are affected . Test different fonts and see if you can narrow it down.

---

