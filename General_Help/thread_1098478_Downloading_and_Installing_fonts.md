---
title: "Downloading and Installing fonts"
date: 2009-03-17
forum: General Help
---

### Post by krome21 on 2009-03-17
I am a newbie. where can i get/download fonts? I wanted to use it in gimp. 

Thanks in advance.

---

### Post by iaculallad on 2009-03-17
For installing the MSCorefonts:

```
sudo apt-get install msttcorefonts
```

---

### Post by jazzgossen on 2009-03-17
You can download fonts from many places on the web. Just try searching for it.

When you have downloaded the fonts (TrueType or PostScript fonts, for example) you need to install them. To do that just for yourself, place the font files in the ~/.fonts/ directory (that is, a subdirectory in your home directory called ".fonts"). Then run the "fc-cache" command.

To install the fonts globally (for all users of your computer), place the files in "/usr/local/share/fonts/" instead, and run "sudo fc-cache".

---

