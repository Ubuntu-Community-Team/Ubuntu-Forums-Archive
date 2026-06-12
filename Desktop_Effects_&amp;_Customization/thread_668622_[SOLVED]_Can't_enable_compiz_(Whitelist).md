---
title: "[SOLVED] Can't enable compiz (Whitelist)"
date: 2008-01-15
forum: Desktop Effects &amp; Customization
---

### Post by Darkade on 2008-01-15
when I try to enable compiz in the command line i get this error
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: //usr/bin/metacity

---

### Post by HermanAB on 2008-02-16
I guess that the mesa library (OpenGL) is missing.

When you see errors like this, try to run the program from a console.  That way, you will be able to see the error messages.  To figure out what to run, right click the icon/menu entry and look for the command then copy and paste it to a console.

Hope that helps!

Herman

---

### Post by Darkade on 2008-02-16
> **HermanAB said:**
> I guess that the mesa library (OpenGL) is missing.

When you see errors like this, try to run the program from a console.  That way, you will be able to see the error messages.  To figure out what to run, right click the icon/menu entry and look for the command then copy and paste it to a console.

Hope that helps!

Herman

:(:( That's the terminal reply :(:( I really don't know where else should I look for.

---

### Post by PurposeOfReason on 2008-02-16
Can you post what graphics card you're using, what driver for it, and your xorg.conf please?

---

### Post by Darkade on 2008-02-16
> **PurposeOfReason said:**
> Can you post what graphics card you're using, what driver for it, and your xorg.conf please?

I'll do that as soon as I can because it's not my computer having this problem it's my girlfriend's computer.:lolflag: thanks

---

### Post by rainwalker on 2008-02-16
Also, you can force Compiz to start using 
```
SKIP_CHECKS=yes compiz
``` 
That should tell you all the things that it's having problems with

---

### Post by Darkade on 2008-05-09
My graphics card had a bad configuration. check
[http://ubuntuforums.org/showthread.php?t=779530](http://ubuntuforums.org/showthread.php?t=779530)
to see how I solved it, hope this helps if you have the same problem :D
:lolflag:

---

