---
title: "how to update the direct x?"
date: 2009-02-23
forum: General Help
---

### Post by Pinejoker on 2009-02-23
could someone help me to update my direct x ubuntu 8.10

---

### Post by binbash on 2009-02-23
??Do you want to update directx at wine?DONT DO it unless you know what you are doing

---

### Post by Pinejoker on 2009-02-23
not really.. but i bought a new video card.. and for some games also..

---

### Post by Yellow Pasque on 2009-02-23
DirectX isn't used in Linux. Windows emulators (like WINE) will use OpenGL for the DirectX Windows programs.

You'll have to upgrade WINE to the devlopment branch if you want the latest DirectX on linux. See: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

(If you're not using WINE, please let us know what you're using).

---

### Post by Pinejoker on 2009-02-23
ahh okay.. on this link.. i can update my direct x to latest?

---

### Post by kaurman on 2009-02-23
Pinejoker, could you please specify what exactly is your goal? If you are trying to make a game run then how is this game called?

As for the link Temüjin gave, this leads to wine hq's download page. Wine is (quote from ubuntu debs text):
> 
Wine is a compatibility layer for running Windows applications on Linux. Applications are run at full speed without the need of cpu emulation. Wine does not require Microsoft Windows, however it can use native system dll files in place of its own if they are available.
This package includes a program loader for running unmodified Windows executables as well as the Wine project's free version of the Windows API for running programs ported from Windows. 

While it is possible to make quite a few games run using Wine, windows is almost definitely a better option compared to linux when it comes to gaming. One of the reasons for that is the fact that many games use directX which is strictly a windows based thing.



K

---

### Post by Pinejoker on 2009-02-23
the reason is i am installing a video card for my linux.. PNY NVIDIA GeForce 8400 GS.. can you help me how to install or work this video card to my linux..

---

### Post by mb_webguy on 2009-02-23
Install envyng-gtk.  Run it in the terminal with "envyng -t", and let it detect and install the appropriate driver for your new card.

As others have said, DirectX is a Windows thing, and doesn't apply to Linux.

---

### Post by yther on 2009-02-23
OK, then you want to forget about the word DirectX (if it is a word at all).  Ignore it, suppress it, expunge it from your thoughts!  :evil:  DirectX is a Windows thing, so if you will not be running Windows games on your system, you don't need it.

What you want is a *graphics driver*.  Most likely, the normal packages in the repositories will handle this card.  You can install them using regular package management tools like Synaptic.

[This guide]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") may be helpful.  I advise you to read it and maybe print it, or keep it open on another computer if you have a spare.  That way if you find yourself staring at a text screen because the driver won't load, you have some resources.

Someone else will probably have other good suggestions.  :)

---

### Post by Pinejoker on 2009-02-23
okay ill try those links sorry guys.. im just having a hard time running my new card.. because i just new fresh installed of my ubuntu XD

---

### Post by Pinejoker on 2009-02-23
do i need to use the cd of my new video card?

---

### Post by mb_webguy on 2009-02-23
No.  Just use envyng, and it will download and install the appropriate driver for you from the nVidia website.

---

