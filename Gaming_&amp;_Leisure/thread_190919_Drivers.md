---
title: "Drivers?"
date: 2006-06-06
forum: Gaming &amp; Leisure
---

### Post by JNowka on 2006-06-06
I have so far installed midi support, TM20 codecs, and several windows and linux based softwares and am happy to say that I now have a new error message while trying to run FF7.

I am told that my graphics card is not supported by DirectX.  I know I havent installed graphics drivers under wine, but when I did try the download it would just say it couldn't do it.

I have a nVidia graphics card with default drivers under linux.  I am using the wine's default for DirectX.  So two questions.  How do I install a windows based DirectX under Wine, and how do I install the nVidia graphics card drivers under Wine.  Any help would be greatly apreciated.

---

### Post by seth0x2b on 2006-06-06
Wine has builtin DirectX drivers by default.
If you want to use your own, copy the drivers to WINE's fake windows directory(~/.wine/drive_c/windows/), then set wine to use them by running "winecfg",and on the "Libraries" tab enter the dll name("dinput.dll" for example) and hit add.That should do the trick(but..as I said, wine already has DirectX).

For the nVidia drivers, do a search on the forum.There are ALOT of threads on this issue.

Cheers

---

### Post by JNowka on 2006-06-07
When looking for the threads you talk about all I see is how to install nVidia drivers under linux.  How would one go about installing the drivers under wine?  Is it neccisary to do so?  Should wine already be using the linux drives instead?

---

### Post by tseliot on 2006-06-07
[QUOTE=JNowka]When looking for the threads you talk about all I see is how to install nVidia drivers under linux.  How would one go about installing the drivers under wine?  Is it neccisary to do so?  Should wine already be using the linux drives instead?[/QUOTE]
Wine does use Linux nvidia drivers. Cedega is a commercial version  of Wine for playing games.

---

