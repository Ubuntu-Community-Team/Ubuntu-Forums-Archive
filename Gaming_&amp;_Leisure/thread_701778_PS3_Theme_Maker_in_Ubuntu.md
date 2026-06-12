---
title: "PS3 Theme Maker in Ubuntu?"
date: 2008-02-19
forum: Gaming &amp; Leisure
---

### Post by Fleck1337 on 2008-02-19
Does anyone know if there is a program that will create PS3 themes for Ubuntu?

If not then is it possible to make themes any other way using Ubuntu?

---

### Post by Dynamic Man on 2010-10-28
I followed the instructions on [http://uk.playstation.com/ps3/support/settings/detail/linked235336/item298356/Create-your-own-PS3-custom-theme/]("http://uk.playstation.com/ps3/support/settings/detail/linked235336/item298356/Create-your-own-PS3-custom-theme/") and used wine (v 1.2) to run the windows binary that came packed with "The PlayStation 3 Custom Theme Guidelines" zip file, which they refer to (downloaded at [http://eu.playstation.com/ps3-custom-themes]("http://eu.playstation.com/ps3-custom-themes")).

The only thing that differed from the instructions in the link above was that it didn't work to just drag n drop the MyTheme.xml file on the p3tcompiler.exe, so i fired up the terminal and wrote

```
cd ~/PS3/PS3_Custom_Theme_v180/
wine p3tcompiler.exe ~/PS3/DynamicManTheme/DynamicManTheme.xml
```

The paths may of course be different on your system, just to be unnecessarily clear. :)

If anyone knows of a better (native) way to compile a PS3 theme on a gnu/linux distribution, please let me know...

---

