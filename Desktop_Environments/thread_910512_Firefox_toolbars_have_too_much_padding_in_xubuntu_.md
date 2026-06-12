---
title: "Firefox toolbars have too much padding in xubuntu 8.04 XFCE"
date: 2008-09-04
forum: Desktop Environments
---

### Post by mrtwice99 on 2008-09-04
I have a pretty much fresh install of xubuntu going in vmware virtual box.  One of the first things I did was install the webdeveloper extension for Firefox.  It worked fine, but I noticed that the toolbar extends off the side of the screen.  I have 1024x768 screen resolution and I don't have this problem on Windows (native) or a Slackware 12.1 install (virtual os) using XFCE.

I have tried adjusting fonts and I can get the fonts small enough that all component of the toolbar appear, but then the fonts are too small to be useful.  I did a screenshot (see the attachment) of the various displays and it actually looks like there is too much padding around the buttons in xubuntu.  That goes for the normal FF toolbars as well as the webdeveloper extension toolbar.

I also tried a fresh copy of FF installed to a local directory and it displayed the same problem.

update:

I installed the kde desktop and FF also has the same problem there.

---

### Post by mali2297 on 2008-09-04
Have you tried changing gtk theme?

Press Alt+F2 to open a run dialog and type
```

xfce-setting-show ui

```
*or* go through the settings menus to find the UI preferences.

---

### Post by mrtwice99 on 2008-09-04
> **mali2297 said:**
> Have you tried changing gtk theme?

Press Alt+F2 to open a run dialog and type
```

xfce-setting-show ui

```
*or* go through the settings menus to find the UI preferences.

Thank you for the quick reply.  Yes, I tried changing the themes.  However, based on your suggestion, I went back and tried all of them.  The one that did the best was xfce-kolors.  But it still had the right most icon cut off.

---

### Post by mali2297 on 2008-09-04
Looking at the screenshot, it seems to me that the font size in Slackware is smaller than in Kubuntu?

---

### Post by mrtwice99 on 2008-09-04
> **mali2297 said:**
> Looking at the screenshot, it seems to me that the font size in Slackware is smaller than in Kubuntu?

Yes, it is.  But I have tried decreasing the font size in the UI settings to no avail.  I have to get it down to about 6pt before the whole bar shows up.  But then the fonts are too small to read.

---

### Post by mrtwice99 on 2008-09-04
> **mali2297 said:**
> than in Kubuntu?

Sorry, its actually an xubuntu screenshot.  The screenshot says kubuntu, but that is wrong.

---

