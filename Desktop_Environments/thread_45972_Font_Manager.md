---
title: "Font Manager?"
date: 2005-07-02
forum: Desktop Environments
---

### Post by FrzzMan on 2005-07-02
Is there any font manager for Ubuntu? An application like Font Book or FontAgent in Mac OS X.

Thanks.

---

### Post by GTvulse on 2005-07-02
[QUOTE=FrzzMan]Is there any font manager for Ubuntu? An application like Font Book or FontAgent in Mac OS X.

Thanks.[/QUOTE]
 No. But that doesn't mean there is none. Debian and derivatives (such as Ubuntu), have a package called defoma (Debiin Font Manager). You can use it to install and deinstall fonts at the system-wide level. Defoma is somewhat esoteric but very powerful; I recommend you explore the documentation before jumping into installing your own fonts (defoma-doc in the base repository).

If you only want to install fonts to be used with Gnome applications, you can do it by creating a directory called ".fonts" (notice the dot) in your home directory, copying the fonts there and then running the command "fc-cache". If using postscript fonts, you only need to copy the PFB and perhaps the AFM files. There is no program under Linux or Unix that uses PFM files (pfm files are used by Windows only).

---

### Post by tcraver on 2006-08-10
> **dradul said:**
> If using postscript fonts, you only need to copy the PFB and perhaps the AFM files. There is no program under Linux or Unix that uses PFM files (pfm files are used by Windows only).

I have a lot of font I purchased that are two files, pfb/pfm in pairs.  Does this mean just the pfb part of the font file will work - or does it really need to be paired together?  And if so, am I just not able to use these fonts?

---

### Post by dangermouse28 on 2006-08-16
From my very limited understanding of fonts, you should be ok with just the .pfb files - try and see!

Although there's little in terms of font manager programs, I've devised my own method. I have 5 font folders: Windows Fonts, Standard Text, Fun Text, Graphic Fonts and Handwriting Fonts. The Windows Fonts folder holds all the fonts typically found in a standard XP installation. The others hold other fonts I've previously used and categorised according to use. While the Windows Fonts folder resides permanently in the .fonts folder (cos I need to be able to access stuff created on the wife's W2k laptop) the others stay in the /home folder. When I need something other than the Windows Fonts, I copy the required folder into the .fonts folder and do fc-cache -fv. When I've finished, I just delete the extra folder and we're back to the start again! 

Fonts can be previewed by double clicking on individual font files (or the OpenOffice font menus). 

I just need to remember to make a note in the File: Properties dialogue box listing any extra fonts used in a document as it might not make much sense if I open a 2 month - old document with a completely different font set loaded! :cool:

---

