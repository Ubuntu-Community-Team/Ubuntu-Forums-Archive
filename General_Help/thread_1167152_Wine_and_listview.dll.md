---
title: "Wine and listview.dll"
date: 2009-05-22
forum: General Help
---

### Post by grtwhiterhyno on 2009-05-22
alrighty then, i've been beating my head against this wall by myself long enough. up to this point i have been able to resolve problems in launching some web development programs, namo's webeditor and freemotion, but webcanvas is giving me a problem. here is what i got at first in terminal:

########:~/.wine/drive_c/Program Files/Namo/WebCanvas 2006/bin$ wine WebCanvas.exe
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 3 lpiArray 0x329410
fixme:richedit:RichEditWndProc_common EM_SETEDITSTYLE: stub
fixme:richedit:RichEditWndProc_common EM_SETEDITSTYLE: stub

but, after replacing the richedit dll files, riched20 & and 32, i still get some kind of failure, this is the message that continues plague me:

########:~/.wine/drive_c/Program Files/Namo/WebCanvas 2006/bin$ wine WebCanvas.exe
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 3 lpiArray 0x329410

i replaced the dll in the same manner and still this junk. the program almost gets all the way open and then spppp! not. i have no idea what to do, i have searched and read yet nothing seems to even explain what is wrong. can i fix it? or am i stuck. appreciate any help i can get.

---

### Post by grtwhiterhyno on 2009-05-23
bump

---

### Post by Ugluk on 2009-05-23
[LISTVIEW_SetColumnOrderArray]("http://msdn.microsoft.com/en-us/library/bb761161(VS.85).aspx")
I'm afraid that the crash of your application is not related to this, for this message changes nothing significant.

---

### Post by grtwhiterhyno on 2009-05-25
then what do you think it is

---

