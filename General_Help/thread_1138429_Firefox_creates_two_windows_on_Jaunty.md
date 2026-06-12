---
title: "Firefox creates two windows on Jaunty"
date: 2009-04-26
forum: General Help
---

### Post by doccolinni on 2009-04-26
I have never seen this error before and I have absolutely no idea what might be causing it. In short, Mozilla Firefox creates two separate windows when I open it - one is its normal one and the other one is... "void". I believe the screenshots will explain it better than I ever could:

[_First screenshot_]("http://img223.imageshack.us/img223/7188/screenshot1iwl.png") shows the "void" window in the upper-left part of the screen. You can see it as a tiny dot in the leftmost edge of the screen, just below the upper panel.

When I minimise Firefox this window will be minimised too, and the "magic lamp" effect (which I've chosen as a minimise effect) will be applied to it too, making it easier to see - [_screenshot_]("http://img126.imageshack.us/img126/238/screenshot2v.png").

The window is also shown in the ring switcher and in any other window switcher I use - [_screenshot_]("http://img223.imageshack.us/img223/3254/screenshot3ixk.png").

Does anyone have *any* idea what might be going on here? I'm completely confused. It doesn't really bother me and it's not causing any other errors, but it's still an unnerving nuisance and I'd like to fix it. Can anyone help, please? :confused:

---

### Post by doccolinni on 2009-04-26
Woah these forums are active... *minibump*

---

### Post by doccolinni on 2009-04-26
Hey, I fixed it! :guitar: 

Although no one wanted to try to help even by giving ideas, I'll share the experience. The window was created by an add-on, called [FoxTab]("https://addons.mozilla.org/en-US/firefox/addon/8879"). It seems that the add-on creates a separate window to render whatever it needs to render when it needs to render anything (like 3D previews of tabs). I disabled that add-on and the "void" window is gone. :)

---

