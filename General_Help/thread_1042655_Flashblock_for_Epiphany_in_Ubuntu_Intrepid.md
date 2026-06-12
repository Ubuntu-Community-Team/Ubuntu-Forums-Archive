---
title: "Flashblock for Epiphany in Ubuntu Intrepid"
date: 2009-01-17
forum: General Help
---

### Post by m83 on 2009-01-17
Hello. I'm trying to install the Flashblock extension in Epiphany by following the [instructions]("http://live.gnome.org/Epiphany/FlashBlock") from the [live.gnome.org wiki]("http://live.gnome.org/"), but it doesn't seem to work no matter where I put the files.

I have Epiphany 2.24.1, xulrunner-1.9.0.5, Adobe Flashplayer 10,0,15,3.

I've tried putting the flashblock.jar and flashblock.manifest in [FONT="Courier New"]/usr/share/epiphany-browser/chrome/[/FONT], [FONT="Courier New"]/usr/lib/xulrunner/chrome[/FONT], [FONT="Courier New"]/usr/lib/xulrunner-1.9.0.5/chrome/[/FONT] (each time adjusting the path in flashblock.manifest to reflect the location of the flashblock.jar), but to no avail.

Any help, or any sugestion as to somehow debug from where Epiphany is loading the extentions would be greatly apreciated.

---

### Post by m83 on 2009-01-18
Nevermind. I solved the problem. The flashblock.manifest for Ubuntu/Debian distributions is different from the other distributions. I corrected flashblock.manifest and it's working now.

---

### Post by n8han on 2009-01-25
By the way the particular directory that works for me is

/usr/lib/xulrunner/chrome

and so the flashblock.manifest reads

```
content flashblock jar:file:///usr/lib/xulrunner/chrome/flashblock.jar!/content/flashblock/ xpcnativewrappers=yes contentaccessible=yes
```

Yay I can read the web again.

---

