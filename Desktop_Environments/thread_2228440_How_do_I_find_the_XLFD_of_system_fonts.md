---
title: "How do I find the XLFD of system fonts?"
date: 2014-06-07
forum: Desktop Environments
---

### Post by AussieGuy on 2014-06-07
Hello,

I have just installed Kubuntu 14.04, 64 bit.  Very nice!   However, some applications (like GNU Emacs) have different menu fonts than say, Konsole or Firefox.  In an effort to coerce Emacs into having nicer menu fonts, I need to change that font using my .Xresources file.  This means I need to find the X Logical Font Description of the system font "Ubuntu 9".  How can I do this?  I've fiddled with xfontsel, but not to much effect.   

Or is there some generic way in which I can ensure that all applications have the same menu fonts?

Thanks very much!
-A.

---

### Post by Erik1984 on 2014-06-07
I don't know if GNU Emacs is a GTK app but KDE has a settings screen (in the System Settings application : Application Appearance > GTK) for the appearance of GTK apps. Hower that doesn't work for me [http://ubuntuforums.org/showthread.php?t=2228079](http://ubuntuforums.org/showthread.php?t=2228079) but maybe you could try changing the settings there to see if it makes any difference.

---

### Post by AussieGuy on 2014-06-08
Thanks for that, however the KDE settings just give me the font name: "Ubuntu", and size: 9.  What I want to find out is the XLFD of this font, so I use it in other applications.  But I can't find out how to do this, or where to search for it.  Any advice would be welcome!  Thanks again.

---

