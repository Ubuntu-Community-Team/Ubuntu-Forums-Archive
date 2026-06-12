---
title: "Default file manager (PCManFM) cannot open .tex files with Texmaker"
date: 2012-08-06
forum: Desktop Environments
---

### Post by InspiredIndividual on 2012-08-06
I am unable to get Texmaker to open .tex files from the file manager. Texmaker is set as the default application to open .tex files in 
~/.local/share/applications/mimeapps.list. However, double-clicking a .tex file does open Texmaker, but not the file itself. The same goes for right-clicking and using a custom command line.

All texmaker commands do work when issued from the command line, so it seems to be a file manager issue. Opening files from withing Texmaker works fine as well. My problem seems to be the same as the one posted [here]("https://sourceforge.net/tracker/index.php?func=detail&aid=3521784&group_id=156956&atid=801864"), but that thread is unresolved so any help would be appreciated.

I am using Lubuntu 12.04 with the texmaker package from the official repositories.

---

### Post by LewisTM on 2012-08-07
I was able to replicate the behavior. The problem lies with the %U found in /usr/share/applications/texmaker.desktop
```
Exec=texmaker %U
```
Texmaker doesn't seem to understand the URL passed by PCManFM - a file:/// formatted location. Changing it to %f (standard filename) fixed the problem for me.

So why does it work with Nautilus and Thunar? That's even more interesting. I ran some tests and found that both file managers ignore the %U and pass a standard filename. A bug or a feature? You call.

Cheers!

---

### Post by InspiredIndividual on 2012-08-16
Well, I don't know...

Anyway, thanks for your help. I was out of town last week so I was unable to try your suggestion before, but it did the trick for me. Thanks!

---

