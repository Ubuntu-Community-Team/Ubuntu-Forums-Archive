---
title: "Shortcuts and unicode problem"
date: 2005-07-30
forum: Desktop Environments
---

### Post by Svictor on 2005-07-30
Hi,
Appearently, on Gnome desktops, the combination of SHIFT+CTRL+<certains keys> is configured to let one enter unicode characters. For example, SHIFT+CTRL+<543> produces this lovely little thing : &#1347;.
For me, the problem is that this behaviour locks a lot of keys which I used (on my previous OS) for shortcuts in some apps like openoffice. For example, I can't use CTRL+SHIFT+<any number> because it is interpreted as the beginning of the code of a unicode character. And on an azerty keyboard, the numbers are already in shift position, so I can't even use CTRL+<number> (since I have to press shift to get the number, and then Gnome thinks I want to type unicode ...). 
This behaviour should be the kind of thing one can disable but I just can't find how. :| Any solution ?
Cheers !

---

### Post by orbit on 2005-10-12
I've been having the same problem.  Shift+Ctrl+[0-9 and A-F] are caught by Gnome instead of the application.

Did you figure it out yet Svictor?

---

### Post by frodon on 2005-10-12
You can manage all your shortcuts with Gconf editor. Open it and go to apps>metacity> you wiil be able to delete unwanted shortcuts. 
Have a look to my [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=42404") if you want to create your own custom keyboard shortcuts.

---

### Post by orbit on 2005-10-12
[QUOTE=frodon]You can manage all your shortcuts with Gconf editor. Open it and go to apps>metacity> you wiil be able to delete unwanted shortcuts. 
Have a look to my [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=42404") if you want to create your own custom keyboard shortcuts.[/QUOTE]

I've looked in apps>metacity>* and can't find anything helpful.  

From the GNOME Keyboard Interaction guidlines for developers ([http://developer.gnome.org/projects/gup/hig/2.0/input-keyboard.html](http://developer.gnome.org/projects/gup/hig/2.0/input-keyboard.html)):
> Use Shift-Ctrl-letter for functions that reverse or extend another function. For example, Ctrl-Z and Shift-Ctrl-Z for Undo and Redo.
[INDENT]**Unicode entry shortcuts**
_Note that you cannot use Shift-Ctrl-A-thru-F or Shift-Ctrl-0-thru-9 for your own purposes, as these combinations are used to enter unicode characters in text fields_.[/INDENT]

Sounds like this is a GNOME thing, and not just metacity.  I've looked around everywhere in Gconf and still haven't found anyway to disable this 'feature'.

Any help would be appreciated.

---

### Post by Alexander Kirillov on 2005-10-12
[QUOTE=Svictor]Hi,
Appearently, on Gnome desktops, the combination of SHIFT+CTRL+<certains keys> is configured to let one enter unicode characters. For example, SHIFT+CTRL+<543> produces this lovely little thing : &#1347;.
For me, the problem is that this behaviour locks a lot of keys which I used (on my previous OS) for shortcuts in some apps like openoffice. For example, I can't use CTRL+SHIFT+<any number> because it is interpreted as the beginning of the code of a unicode character. And on an azerty keyboard, the numbers are already in shift position, so I can't even use CTRL+<number> (since I have to press shift to get the number, and then Gnome thinks I want to type unicode ...). 
This behaviour should be the kind of thing one can disable but I just can't find how. :| Any solution ?
Cheers ![/QUOTE]

Can't give precise answer - but it is definitely coming from xkb (xkeyboard extension). Probably can be overriden by a suitable option in xorg.conf file (try  "nodeadkeys") - search google for detailed instructions.

---

### Post by orbit on 2005-10-12
[QUOTE=Alexander Kirillov]Can't give precise answer - but it is definitely coming from xkb (xkeyboard extension). Probably can be overriden by a suitable option in xorg.conf file (try  "nodeadkeys") - search google for detailed instructions.[/QUOTE]

I tried using nodeadkeys in my /ect/X11/xorg.conf file, but after restarting I got an error dialog (8 times).  They said:
[INDENT]Error activating XKB configuration.
This can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <br>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>[/INDENT]

The results from those two calls are:
$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "us", "nodeadkeys", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "us", "", "altwin:meta_win"

$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us  nodeadkeys]
 model = pc104
 overrideSettings = false
 options = []

---

### Post by Alexander Kirillov on 2005-10-13
[QUOTE=orbit]I tried using nodeadkeys in my /ect/X11/xorg.conf file, but after restarting I got an error dialog (8 times).  They said:
[INDENT]Error activating XKB configuration.
This can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <br>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>[/INDENT]

The results from those two calls are:
$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "us", "nodeadkeys", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "us", "", "altwin:meta_win"

$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us  nodeadkeys]
 model = pc104
 overrideSettings = false
 options = [][/QUOTE]

sorry -out of my depth here.

---

