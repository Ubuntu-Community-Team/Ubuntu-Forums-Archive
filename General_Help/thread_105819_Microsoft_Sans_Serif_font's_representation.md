---
title: "Microsoft Sans Serif font's representation"
date: 2005-12-19
forum: General Help
---

### Post by Ubuntooid on 2005-12-19
Please help me with following problem - incorrect representation of Microsoft Sans Serif font. I had installed msttcorefonts package and after making sure that the font is not included into it I had copied that font's file (micross.ttf) from MS Windows XP to directory ~/.fonts. I had ran "fc-cache -f" command from terminal and rebooted my Breezy. The font became accessible in applications, I had selected it in Gnome's utility, turned off smoothing, selected full hinting and left untouched resolution - 96 dpi. Finally, I have problems with representation of some letters, especially in cyrillic's letter that have something like umlaut at its top. I'm attaching a screenshot with application (gedit) that uses this font:

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=4684&stc=1&d=1135003783[/IMG]

All other fonts are representing perfectly, including ones installed with msttcorefonts and Tahoma copied to ~/.fonts.

That's what I had tried to do and what didn't help me:

 - I had selected another hinting, with slight and medium I had the same result, with hinting turned off - these defects disappeared, but without hinting fonts are looking terribly;
 - According to HOWTO at [http://www.ubuntuforums.org/showthread.php?t=20976](http://www.ubuntuforums.org/showthread.php?t=20976), I had changed resolution in xorg.conf to 96 dpi;
 - According to the same HOWTO I had tried to change options in "dpkg-reconfigure fontconfig", but the best what I had was disappearing defects with global decrease of fonts representation quality, almost like without hinting;
 - I had tried to take another version of micross.ttf from Windows 2000, Windows 2000 SP4, Windows XP SP2, but nothing had changed.

I hope that I will not be accused in excessive adherence to Microsoft, but I had used this font as main in operating systems almost 10 years and now I don't perceive correctly an operating system with another fonts. :(

---

### Post by Pigmudgeon on 2005-12-19
I successfully replaced the Gnome fonts with Microsoft's for the same reason -- I also think MS has better fonts, mainly because they've spent millions of dollars since 1992 on usability issues. 

I am pretty sure your problem is with the Cyrillic part of the symbol set. I know a little Russian and have had two or three occasions to use Cyrillic, and also had problems. The problems are not so severe with the specifically Unicode fonts (like MS Arial Unicode), but the screen fonts for those are terrible. 

You may be out of luck, although Microsoft's Knowledge Base *may* have the answer you're looking for. 

--p!

---

### Post by Ubuntooid on 2005-12-20
[QUOTE=Pigmudgeon]I successfully replaced the Gnome fonts with Microsoft's for the same reason -- I also think MS has better fonts, mainly because they've spent millions of dollars since 1992 on usability issues. 

I am pretty sure your problem is with the Cyrillic part of the symbol set. I know a little Russian and have had two or three occasions to use Cyrillic, and also had problems. The problems are not so severe with the specifically Unicode fonts (like MS Arial Unicode), but the screen fonts for those are terrible. [/QUOTE]

Can you tell me please, do you have the same slight defects with Microsoft Sans Serif that is shown at screenshot with latin uppercase letters "M", "Q", lowercase "x" and digits "8" and "9"? Although one of cyrillic letters has more defects than all of other and so defects with cyrillic are more visible, but there are defects in latin letters too. Moreover, defects with "M" and "x" are identical in both alphabets and "8" and "9" are common. I suppose there must be one reason for distortion in both alphabets.

> 
You may be out of luck, although Microsoft's Knowledge Base *may* have the answer you're looking for. 

--p!

I have scanned through it, but I didn't see anything like this problem. And I don't think that Microsoft would attend to problems with their fonts in Linux, especially while there is no any similar problems in their own operating system. :(

---

