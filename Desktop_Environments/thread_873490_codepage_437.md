---
title: "codepage 437"
date: 2008-07-29
forum: Desktop Environments
---

### Post by resolv_25 on 2008-07-29
I have problem setting code page 437 on Ubuntu 7.10 -Gutsy.

I'm connected to another computer's application via Telnet.
From windows environment, I use Netterm with fonts *cur437 *(OEM/DOS), and it is working fine.

From Ubuntu, I've tried Putty which has a character setting (I put on cp1250, as I'm using this setting on another application and getting correct fonts), 
and possibility of choosing fonts, but don't have such a font.

I downloaded MS fonts 
*$sudo apt-get install msttcorefonts*
so, I have Arial, Courier etc.

The easiest way could be to paste correct fonts into fonts:///
but I can't find this fonts on web . . .

---

### Post by wannadumpwindows on 2008-07-29
Your fonts are in:

```
/usr/share/fonts
```

---

### Post by resolv_25 on 2008-07-29
> **wannadumpwindows said:**
> Your fonts are in:

```
/usr/share/fonts
```

Yes, I've found ibm-cp437 within, actually;
*/usr/share/fonts/X11/encodings*
I've extracted it, but how shall I load this font to be visible on the list of fonts, or how to load it when I start telnet from command line, or from putty ?

---

