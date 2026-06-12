---
title: "Script that automatically installs Vista fonts."
date: 2008-03-15
forum: Desktop Effects &amp; Customization
---

### Post by phrostbyte on 2008-03-15
Self explanatory. Downloads the fonts directly from Microsoft themselves. Windows Vista not required for this script to work. Please ensure you are in accordance with all the local laws of your region or country before using this script.

To execute (from the desktop) copy and paste this into a terminal:

chmod +x ~/Desktop/vista_fonts.sh; sudo bash ~/Desktop/vista_fonts.sh

The script may be safely deleted after successful installation.

Enjoy.

Edit: New version uploaded which adds better error detection.

:popcorn:

---

### Post by phrostbyte on 2008-04-11
New version created which will work around many errors people may have. It's a pretty complex script now. :)

---

### Post by SEMW on 2008-04-11
Good job!  As it happens, I already have the fonts, so I'm posting in here to ask whether anyone else has the problem that with the Freetype font renderer set to 'native', these fonts look terrible at small point sizes?  Specifically, Calibri and Cambria look terrible at less than 16pt; Consolas at less than 13pt.  (By 'terrible' I mostly mean 'not antialiased, ligatures show up wrongly, etc.').  (The problem doesn't occur with the autohinter, since everything's ridiculously antialiased; but that makes most fonts (Bitstream Vera etc.) look awful).  Is it just my system? **Edit:** [Apparantly not.]("http://ubuntuforums.org/showthread.php?p=4697776#post4697776")

---

### Post by phrostbyte on 2008-04-11
> **SEMW said:**
> Good job!  As it happens, I already have the fonts, so I'm posting in here to ask whether anyone else has the problem that with the Freetype font renderer set to 'native', these fonts look terrible at small point sizes?  Specifically, Calibri and Cambria look terrible at less than 16pt; Consolas at less than 13pt.  (By 'terrible' I mostly mean 'not antialiased, ligatures show up wrongly, etc.').  (The problem doesn't occur with the autohinter, since everything's ridiculously antialiased; but that makes most fonts (Bitstream Vera etc.) look awful).  Is it just my system? **Edit:** [Apparantly not.]("http://ubuntuforums.org/showthread.php?p=4697776#post4697776")

Yes, it seems to be a problem with some applications. Interestingly OOo doesn't seem to have a problem with the Vista fonts.

---

### Post by SEMW on 2008-04-12
> **phrostbyte said:**
> Yes, it seems to be a problem with some applications. Interestingly OOo doesn't seem to have a problem with the Vista fonts.
That's strange, since I have the same problems with the fonts on OOo as in applications.  I've attached a screenshot with Calibri and Cambria -- you can see that at 13.5pt it's antialiased but with inconsistent weight, 14pt and 14.5pt aren't antialiased at all, and 15pt is heavily antialiased; which is the same as with the Gnome interface font chooser.

Though, that said, I can't seem to emulate the ligatures problem in OOo, the one that you see if you choose Calibri as the email display font in Evolution (any combinations like tf, fi, tt etc. appear in boldface non-antialised).

I'm using OOo 2.4.0 on the Hardy beta, incidentally; if you're using OOo 2.3, maybe they've changed the way it renders fonts?

---

### Post by phrostbyte on 2008-04-28
I've noticed this behavior lately. Do you know if there is a bug report on it?

---

### Post by DrAhorro on 2008-05-13
> **SEMW said:**
> I'm posting in here to ask whether anyone else has the problem that with the Freetype font renderer set to 'native', these fonts look terrible at small point sizes?  Specifically, Calibri and Cambria look terrible at less than 16pt; Consolas at less than 13pt.  (By 'terrible' I mostly mean 'not antialiased, ligatures show up wrongly, etc.')

Add this to your [FONT="monospace"]~/.fonts.conf[/FONT] file

```
    <match target="font" >
         <edit name="embeddedbitmap" mode="assign">
             <bool>false</bool>
         </edit>
    </match>
```

---

