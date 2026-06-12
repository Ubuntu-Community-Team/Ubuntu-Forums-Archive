---
title: "gnome terminal/screen/irssi-text"
date: 2006-02-21
forum: Desktop Environments
---

### Post by rehpotsirhc on 2006-02-21
when using a screen'd irssi session in gnome terminal, the screen keeps blanking itself and getting progressively more corrupted, eating more and more cpu until it finally crashes and burns at 99%. anybody experienced this problem or know of a fix?

---

### Post by kaamos on 2006-02-21
I have experinced the screen corruption. If you are talking about most of the text disappearing? Pressing ctrl+L sometimes helps but I normally just use a keyboard shortcut to go to fullscreen and back. The other symptoms I have not seen..

Terminal (xfce) has the same screen corruption problem btw. I'd be happy if someone would like to point me to a terminal app with hyperlink support that works well with screen/irssi.

---

### Post by engla on 2006-02-21
I have seen this problem, at least the part where the gnome-terminal suddenly grabs 97% of CPU and grinds to a halt (you type alt+f2 and make it stop, and thank screen for saving your session)

It quite infrequent though, I have no idea why this is happening.

---

### Post by ardchoille on 2006-02-21
[QUOTE=rehpotsirhc]when using a screen'd irssi session in gnome terminal, the screen keeps blanking itself and getting progressively more corrupted, eating more and more cpu until it finally crashes and burns at 99%. anybody experienced this problem or know of a fix?[/QUOTE]
I have this exact problem and I think, from I have seen and heard, that the problem is the fault of gnome-terminal. I solved this problem by installing rxvt-unicode and using that instead of gnome-terminal. to make rxvt look prettier, add the following to your ~/.Xdefaults file - or create the file if you don't have it and insert the following:

```

urxvt.background:black
urxvt.foreground:grey
urxvt.cursorBlink:true
urxvt.scrollBar:false
urxvt.scrollBar_right:false
urxvt.saveLines:32767
urxvt.font: xft:Courier 10 Pitch-11
urxvt.boldFont: xft:Courier 10 Pitch-11:bold
urxvt.geometry:110x30

```

You can tweak those settings to meet your needs, but rxvt looks very nice and works great with irssi and screen. See a screenshot below.

---

