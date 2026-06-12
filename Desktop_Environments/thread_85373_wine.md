---
title: "wine"
date: 2005-11-02
forum: Desktop Environments
---

### Post by miam on 2005-11-02
hey ,

  to be 100% with Ubuntu I just need to get a program I use to visit  my banks'site , working .

 I installed "wine" without problems [as "sudo"] .   I put the setup.exe file in /.wine/drive-c and runned it [as "sudo"] . At the end of the installation I got this message in the shell :

[B]"err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\CTHLNET55\\launch32.exe") failed, error 126

err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink

err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\CTHLNET55\\CORTNET.ICO") failed, error 193"[/B]

  Can anybody tell me what to do to try fixing these problems ? Thanks for your help .

---

### Post by carney1979 on 2005-11-02
You posted in the wrong forum.

You might try posting this in desktop support instead of here, customization tips & tricks.

David

---

### Post by dcstar on 2005-11-04
[QUOTE=miam]hey ,

  to be 100% with Ubuntu I just need to get a program I use to visit  my banks'site , working .

 I installed "wine" without problems [as "sudo"] .   I put the setup.exe file in /.wine/drive-c and runned it [as "sudo"] . At the end of the installation I got this message in the shell :
.......[/QUOTE]
Wine - and apps run under Wine - are not meant to be run under "sudo".

Try them again as a normal user.

---

### Post by miam on 2005-11-04
if I configure WINE (winecfg) as a normal user and run "wine setup.exe"  it looks worse : 2 more errors on the first and the last lines ,  "fixme ..." and "cp: ..." .

[B]fixme:font:load_VDMX Failed to retrieve vTable
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\CTHLNET55\\launch32.exe") f ailed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\CTHLNET55\\CORTNET.ICO") fa iled, error 193
cp: ne peut cr&#233;er le fichier r&#233;gulier `/home/mm/.gnome/apps/Wine/Cortal Trader H ome Line v5.5.xpm': Permission non accord&#233;e
[/B]
it says I don't have the rights to create a regular file  "/home/  /.xpm" 

before running this installation program  I tried another one : "hddhealth" ; I got it installed allright .

---

