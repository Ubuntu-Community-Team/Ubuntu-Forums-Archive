---
title: "WINE 0.9.3 and Photoshop 7.0"
date: 2005-12-09
forum: General Help
---

### Post by detyabozhye on 2005-12-09
I updated my WINE today and now Photoshop 7.0 is broken. I tried reinstalling Phostoshop, then redoing the whole WINE configuration, and nothing worked. Any ideas? Currently I'm installing Photoshop CS, but the install is soooooooooo slow, we'll have to see what happens.

Edit: CS didn't work either.

---

### Post by detyabozhye on 2005-12-09
K, here's what I get wehn trying to run Potoshop 7.0
```
fixme:actctx:QueryActCtxW stub!
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7fa7de2c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x7fa7de2c,0x00000000), stub!
fixme:mscms:EnumColorProfilesA ( (nil), 0x7fa7e694, 0x7fa7e1ac, 0x7fa7e6f4, 0x7fa7e704 ) stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7fa7de34,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x7fa7de34,0x00000000), stub!
fixme:mscms:EnumColorProfilesA ( (nil), 0x7fa7e69c, 0x7fa7e1b4, 0x7fa7e6fc, 0x7fa7e70c ) stub
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub

```
Help plz

---

### Post by detyabozhye on 2005-12-09
Has anybody even noticed that WINE 0.9.3 is out and it breaks Photoshop 7?

---

### Post by magnusbb on 2005-12-10
I have upgraded to 0.9.3 and all my current applications work, so there's nothing wrong with the package itself. I have not installed Photoshop 7.0 in WINE though.

I have a separate environment (Crossover 5) running Photoshop 7 and Office 2003.

---

### Post by Perfect Storm on 2005-12-10
Running PS7 through crossover office, later next year they'll support PS CS

---

### Post by Rackerz on 2005-12-10
Crossover Office is the best way to go for running Win apps at the moment i think.

---

### Post by Breepee on 2005-12-10
Crossover doesn't even support CS2??? Sjeez...

---

### Post by YokoZar on 2005-12-10
[QUOTE=detyabozhye]Has anybody even noticed that WINE 0.9.3 is out and it breaks Photoshop 7?[/QUOTE]
If this is true, it's a serious issue called a regression.

Can you please report exactly what broke to the [wine-devel](http://winehq.org/site/forums) email list?  We'd really appreciate it.

You can also post a test result for Photoshop 7 at it's page in the Application's database: [http://appdb.winehq.org/appview.php?versionId=1336](http://appdb.winehq.org/appview.php?versionId=1336)

---

### Post by detyabozhye on 2005-12-10
K, thanks, I will.
I also wanted to mention that PS CS works under WINE 0.9.2 (though the installation is somewhat messed up), but is broken under 0.9.3 also.

---

