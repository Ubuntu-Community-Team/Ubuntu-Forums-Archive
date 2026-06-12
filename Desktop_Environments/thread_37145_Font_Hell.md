---
title: "Font Hell"
date: 2005-05-26
forum: Desktop Environments
---

### Post by K3yMaster on 2005-05-26
Hi,

I've installed Ubuntu (with Kubuntu desktop), but I'm having problems with fonts looking either extremely ugly (no anti aliasing) or looking blurry (with anti aliasing + hinting).

I've been reading lots and lots of forum threads about this topic, but none seem to help my situation.

I'm using a LCD panel (1280x768 Widescreen), and would like a result similar to what I get in Windows (the forbidden word, I know :p)


Can anyone help?

---

### Post by philipacamaniac on 2005-05-26
Have you tried ```
sudo dpkg-reconfigure fontconfig
``` to enable Autohinting rather than Bytecode?

---

### Post by buldir on 2005-05-26
Try here:

[http://ubuntuforums.org/showthread.php?t=23426&highlight=fonts](http://ubuntuforums.org/showthread.php?t=23426&highlight=fonts)

and

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=226046](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=226046)

I recommend reading all the posts before trying stuff.  My post at the bottom of the second one above, is a little more involved.  Regardless, this will give you the "crisp" (non-antialiased) fonts that look decent on an LCD screen...like the default "look" in Windows.

---

### Post by K3yMaster on 2005-05-26
[QUOTE=philipacamaniac]Have you tried ```
sudo dpkg-reconfigure fontconfig
``` to enable Autohinting rather than Bytecode?[/QUOTE]

Yes I tried that, but no go :(


I will try to do as you suggest buldir.. I'm more than happy if I can get the result that you got by compiling freetype yourself.

---

### Post by buldir on 2005-05-26
Here is probably a good start:

[http://www.ubuntuforums.org/showthread.php?t=20976&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=20976&page=1&pp=10)

---

