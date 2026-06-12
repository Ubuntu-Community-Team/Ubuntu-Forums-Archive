---
title: "Removing fonts wants to remove Xubuntu"
date: 2020-10-26
forum: Desktop Environments
---

### Post by xendistar2 on 2020-10-26
I am using Xubuntu 20.04

I have a lot of fonts installed on my laptop, there is also a lot of Arabic fonts like   fonts-noto-ui-core, fonts-noto-hinted, fonts-noto-core. How do I remove them without removing Xubuntu.

I tried to remove the fonts with aptitude but got the following error

```
sudo aptitude remove fonts-noto-hintedThe following packages will be REMOVED:  
  fonts-noto-core{u} fonts-noto-hinted fonts-noto-ui-core{u} 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 41.5 MB will be freed.
The following packages have unmet dependencies:
 xubuntu-default-settings : Depends: fonts-noto-hinted but it is not going to be installed
The following actions will resolve these dependencies:


     Remove the following packages:                   
1)     xubuntu-core [2.233 (focal, now)]              
2)     xubuntu-default-settings [20.04.4 (focal, now)]
3)     xubuntu-desktop [2.233 (focal, now)]           


     Leave the following dependencies unresolved:     
4)     xubuntu-core recommends fonts-noto-hinted      
5)     xubuntu-desktop recommends fonts-noto-hinted  
```

I allowed aptitude to offer other solutions but none met removing the noto fonts and leaving xubuntu intact.

Any suggestions

---

### Post by CelticWarrior on 2020-10-26
My suggestion is to leave them alone.
And Noto is not Arabic.

---

### Post by Holger_Gehrke on 2020-10-27
The 'noto' fonts cover a lot of Unicode. Their name is short for 'no tofu', with 'tofu' being a nickname for the square with the hexadecimal code point of a character you get if you don't have a glyph for a character. So there's not only Arabic script in there but also Latin, Kyrillic, Greek and much, much more. This font family is often used as a fall back for other specialised fonts so you at least get something readable instead of lots of 'tofu'. You can check out what is in that font by using the character table application, selecting the font and activating 'only show glyphs from font' under view.

The xubuntu-desktop and xubuntu-core packages are completely virtual, their job is to pull in the rest of the system through dependencies. Since these dependencies are marked as 'manually installed' if installed during system installation unstalling xubuntu-core and xubuntu-desktop is not a real problem. 

This is not the case for xubuntu-default-settings. This package contains among other things the configuration for the display manager and removing that will get you into real trouble.

Holger

---

