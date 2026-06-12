---
title: "remove ubuntu-restricted-extras fonts (8.04)"
date: 2009-03-04
forum: General Help
---

### Post by gms5002 on 2009-03-04
Hello,

I just installed the ubuntu-restricted-extras package in order add support for some audio formats.  The audio is working fine now, however I've noticed that it has changed some fonts on me.  Most notably the default font in Firefox.  Is there an easy way to roll this change back (or can I remove ubuntu-restricted-extras and just install the audio/video part of it)?

Thanks!

---

### Post by solwic on 2009-03-04
> **gms5002 said:**
> Hello,

I just installed the ubuntu-restricted-extras package in order add support for some audio formats.  The audio is working fine now, however I've noticed that it has changed some fonts on me.  Most notably the default font in Firefox.  Is there an easy way to roll this change back (or can I remove ubuntu-restricted-extras and just install the audio/video part of it)?

Thanks!

```
 sudo apt-get remove ubuntu-restricted-extras 
``` should get rid of the whole thing, but there has to be a way to just remove the fonts.  

EDIT:  The package name is msttcorefonts.  You could try removing that, though I don't know if it would mess anything else up.

```
 sudo apt-get remove msttcorefonts
``` should do it.

Also, did you try resetting the default font?  Right click on desktop, change desktop background, fonts.  

Good luck!

---

### Post by bekind2thenoob on 2009-03-04
the package is called microsoft core fonts in intrepid i assume its sumthing similar in the lts just search in add/remove.

---

### Post by Idaho Dan on 2009-03-04
You can also change your font in Firefox.
Select edit, preferences, and then content.

---

### Post by gms5002 on 2009-03-04
> **jrock612 said:**
> ```
 sudo apt-get remove ubuntu-restricted-extras 
``` should get rid of the whole thing, but there has to be a way to just remove the fonts.  

EDIT:  The package name is msttcorefonts.  You could try removing that, though I don't know if it would mess anything else up.

```
 sudo apt-get remove msttcorefonts
``` should do it.

Also, did you try resetting the default font?  Right click on desktop, change desktop background, fonts.  

Good luck!

Removing the msttcorefonts did the trick.  Thanks!

---

### Post by solwic on 2009-03-04
> **gms5002 said:**
> Removing the msttcorefonts did the trick.  Thanks!

My pleasure.  

Welcome to the light.  :)

---

