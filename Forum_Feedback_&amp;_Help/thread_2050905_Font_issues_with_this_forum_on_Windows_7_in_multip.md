---
title: "Font issues with this forum on Windows 7 in multiple browsers"
date: 2012-08-31
forum: Forum Feedback &amp; Help
---

### Post by specialcase on 2012-08-31
See this screenshot:

[http://i.imgur.com/ksiAD.png](http://i.imgur.com/ksiAD.png)

The font is making every post here almost completely unreadable.  The issue shows up in Firefox, Opera, and Google Chrome (NOT in IE though - go figure).

The "Ubuntu" font in the 'body' CSS style is the cause.  Removing it with Firebug makes the problem go away for me.

---

### Post by coffeecat on 2012-09-01
The font rendering in your screenshot looks far worse than in my Windows 7 installation. Try enabling cleartype, which should have been enabled by default anyway in Windows 7. With default font settings in Windows 7 the forum renders well for me, with only slight jaggedness in the bold fonts.

I found that rendering of the bold type was better if I installed the Ubuntu font family locally. You can download a zip file of the ttf files here:

[http://font.ubuntu.com/](http://font.ubuntu.com/)

---

### Post by specialcase on 2012-09-01
Installing the Ubuntu font set worked right away - no need for ClearType.  ClearType makes fonts display worse on my machine, so I disabled it when I first installed Win7 and promptly forgot about that change.

Now I've got some new fonts to play with.

---

