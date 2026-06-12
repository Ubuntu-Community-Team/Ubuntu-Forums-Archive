---
title: "How to Disable Background Titlebar Transparency in Compiz"
date: 2009-09-08
forum: Desktop Environments
---

### Post by Joseph Schwenker on 2009-09-08
Hi everyone!  I have decided to give compiz another shot, for now at least.  :P  However, I would like to disable the background windows' titlebar transparency.  I cannot find an option in Compiz to do this, and would like to know how.  Thanks in advance!

---

### Post by SoftwareExplorer on 2009-09-08
Are you using emerald? Or you just are using compiz (that's most likely the case if you don't know)?

---

### Post by Joseph Schwenker on 2009-09-08
> **SoftwareExplorer said:**
> Are you using emerald? Or you just are using compiz (that's most likely the case if you don't know)?

I'm using Compiz.  I remember reading something another post about some setting in gconf or a terminal command that could disable the transparency.  Thanks for the reply!

---

### Post by ninjapirate89 on 2009-09-08
Edit -> May my irrelevant comment be stricken from the record.

---

### Post by SoftwareExplorer on 2009-09-08
> **Joseph Schwenker said:**
> I'm using Compiz.  I remember reading something another post about some setting in gconf or a terminal command that could disable the transparency.  Thanks for the reply!

Well, one option would be to use emerald because it lets you tweak those colors, so you could make them not transparent if you want. I don't know about the gconf, but maybe someone else will?

---

### Post by Josh D on 2010-04-05
You need to adjust a setting in Metacity.  See this blog post for instructions:  [http://subbass.blogspot.com/2009/08/adjust-titlebar-transparency-in.html]("http://subbass.blogspot.com/2009/08/adjust-titlebar-transparency-in.html")

[INDENT]Press alt+F2 and in the run dialog enter:

gconf-editor

Navigate in the left hand tree to the branch /apps/gwd/

The two values we are interested in are :

metacity_theme_opacity which affects inactive window titlebars
metacity_theme_active_opacity which affects active windows

A setting of 1 will make the title-bars solid while 0.75 is the default at three quarters opacity.[/INDENT]

---

### Post by asmoore82 on 2010-04-06
Thank you Josh!!

I did not know this at all, but taking Josh's input, the "one-shot" command
to turn off titlebar transparency would be:
```
gconftool-2 --set /apps/gwd/metacity_theme_opacity --type float 1
```

---

### Post by Joseph Schwenker on 2010-05-05
Excellent!  Thanks a bunch!  I am forever indebted to you, Josh.

---

