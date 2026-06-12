---
title: "Mupen64 Plugin help"
date: 2010-09-29
forum: Gaming &amp; Leisure
---

### Post by HeroKing on 2010-09-29
I downloaded a new plugin I want to use for Mupen64 and I found what I believe to be the right directory ```
usr/share/Mupen64/config
``` and I put in the .dll and .ini file needed, but it's not showing up when I open the program. Is this some ubuntu bug that can't be fixed, or can I use my plugin somehow?

---

### Post by Justin_Bailey on 2010-09-29
Linux doesn't use dll files for plugins.  You'll either need to compile the plugin on your own or find a pre-compiled .so library.
In addition as far as I can tell plugins are stored in the /usr/share/mupen64plus/plugins/ directory. (or possibly /usr/local/share/mupen64plus/plugins/ depending on your install method)

---

