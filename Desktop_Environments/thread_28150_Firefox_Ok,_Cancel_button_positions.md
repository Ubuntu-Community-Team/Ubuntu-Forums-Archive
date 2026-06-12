---
title: "Firefox Ok, Cancel button positions"
date: 2005-04-19
forum: Desktop Environments
---

### Post by griphiam on 2005-04-19
Ok, this is really bugging me.  On windows Firefox, "OK" is on the left and "Cancel" is on the right.  But in Linux (and only Firefox it seems, because KDE is the other way), "Cancel" is on the left and "OK" is on the right.

Is there *any* way to swap them?

*Solution* 

Found this over in Gentoo forums:

In your chrome folder in ~/.mozilla/firefox/*.default/chrome/ copy userChrome-example.css to userChrome.css and add the following lines:

```
.dialog-button-box { -moz-box-direction: reverse; -moz-box-pack: right; }
.dialog-button-box spacer { display: none !important; } 
```

---

### Post by ltmon on 2005-04-19
This firefox theme is made to better integrate firefox into KDE.

[http://www.kde-look.org/content/show.php?content=11442](http://www.kde-look.org/content/show.php?content=11442)

The summary on the kde-look website tells you how to swap the button order to match the rest of KDE.

Cheers,
L.

---

### Post by griphiam on 2005-04-19
Found a fix in the Gentoo forums.  See first post.

The theme suggestion above didn't seem to to work.  I couldn't find the button option to reverse them. 

Thanks!

---

### Post by vanaedium on 2005-04-19
simply
[http://www.polinux.upv.es/mozilla/temas.php?idioma=en](http://www.polinux.upv.es/mozilla/temas.php?idioma=en)
you'll find cool themes for ffx and tb in double version, you can download it and choose the rev one
Bye :-)

---

