---
title: "no 8x16 font in gnome-terminal"
date: 2005-10-21
forum: Desktop Environments
---

### Post by dsquared on 2005-10-21
I'm using Breezy, and I want to use the "8x16" font (found in xfonts-konsole and elsewhere) in gnome-terminal, but Gnome won't recognize it.

I've installed xfonts-konsole, xfonts-terminus and console-terminus as detailed  [here]("http://www.ubuntuforums.org/showthread.php?t=14275"), but the fonts don't show up. I've run dpkg-reconfigure fontconfig, I've checked the /etc/fontconfig directory, I've tried putting the font in ~/.fonts, but the font never shows up in the list of fonts.

This worked fine in Debian unstable. It also works on a Red Hat FC3 box that I use at work. Any suggestions? I can't get by without this font in my terminal!

---

### Post by dsquared on 2005-10-23
Fixed! :KS 

The problem is that fontconfig is not looking in the proper directory. xfonts-konsole installs its fonts into /usr/X11R6/lib/X11/fonts/misc, which isn't indexed by fontconfig. The solution is to add a file "/etc/fonts/local.conf" with the contents:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<!-- Font directory list -->

<dir>/usr/X11R6/lib/X11/fonts/misc</dir>

</fontconfig>
```
...and then run ```
sudo fc-cache
``` Then the "8x16" font will be available as "Console".

---

