---
title: "default font path problem in Kubuntu..."
date: 2006-02-16
forum: Desktop Environments
---

### Post by chugru on 2006-02-16
Hi, All...

I appear to have a font path problem preventing me from opening vncserver:```
Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.
Couldn't start Xtightvnc process.


```

I have 2 questions...

What file is the vncserver script?

Hoe do I find the correct "fontPath"?

Thanks...

---

### Post by jbaloul on 2006-03-01
same problem here....

Heeeellllllppppp


(breezy server install)

---

### Post by jbaloul on 2006-03-01
got it!

[http://ubuntuforums.org/showpost.php?p=470564&postcount=5](http://ubuntuforums.org/showpost.php?p=470564&postcount=5)

add this to /etc/vnc.conf

$fontPath .= "/usr/share/X11/fonts/misc/,";
$fontPath .= "/usr/share/X11/fonts/75dpi/:unscaled,";
$fontPath .= "/usr/share/X11/fonts/100dpi/:unscaled,";
$fontPath .= "/usr/share/X11/fonts/Type1/,";
$fontPath .= "/usr/share/X11/fonts/Speedo/,";
$fontPath .= "/usr/share/X11/fonts/75dpi/,";
$fontPath .= "/usr/share/X11/fonts/100dpi/,";
$fontPath .= "/usr/share/X11/fonts/freefont/,";
$fontPath .= "/usr/share/X11/fonts/sharefont/";

---

