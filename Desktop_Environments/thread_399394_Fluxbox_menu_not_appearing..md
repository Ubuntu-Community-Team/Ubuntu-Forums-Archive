---
title: "Fluxbox menu not appearing."
date: 2007-04-02
forum: Desktop Environments
---

### Post by Nonni on 2007-04-02
Hi,
I have this weird problem while running fluxbox,
when I right click on the desktop nothing happens, but I can right click on f.ex. the slit and that works fine, shows the toolbar menu. Everything works just fine except the menu.

It worked ok before and usually works ok if I delete everything from ~/.fluxbox except the startup file and restart, but it usually stops working after a few restarts.

I deleted my menu file so I've got the default generated menu

my log file
> ------------------------------------------
Log File: /home/nonni/.fluxbox/log
Fluxbox version: 1.0rc3
Compiled: Apr  1 2007 00:28:49
Compiler: GCC
Compiler version: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)

Defaults:
    menu: /usr/local/share/fluxbox/menu
   style: /usr/local/share/fluxbox/styles/Clean
    keys: /usr/local/share/fluxbox/keys
    init: /usr/local/share/fluxbox/init

Compiled options (- => disabled): 
-DEBUG
EWMH
GNOME
-IMLIB2
KDE
-NLS
REMEMBER
-RENDER
SHAPE
SLIT
TOOLBAR
-XFT
-XINERAMA
-XMB
XPM

------------------------------------------
Fluxbox: There is no background option specified in this style. Please consult the manual or read the FAQ.

my apps file
> 
[startup] {amsn}
[startup] {conky -c ~/configs/conkyrc-gon} 


My startup file
> exec /usr/local/bin/fluxbox -log ~/.fluxbox/log

---

### Post by kellemes on 2007-04-02
In ~/.fluxbox/init there should be a reference to the menu-file you want to use, is it there?
The menu-file obviously has to be there also, is it?
If not, you should use fluxbox-generate_menu to generate a new menu, better yet, get mmaker ([http://menumaker.sourceforge.net/](http://menumaker.sourceforge.net/)) to generate an even more complete menu..

---

### Post by Nonni on 2007-04-02
Thanks for your answer.

Here's my init file
> session.screen0.slit.placement:	BottomRight
session.screen0.slit.direction:	Vertical
session.screen0.slit.onTop:	False
session.screen0.slit.autoHide:	False
session.screen0.tab.placement:	Top
session.screen0.tab.alignment:	Left
session.screen0.tab.rotatevertical:	True
session.screen0.toolbar.onTop:	False
session.screen0.toolbar.autoHide:	False
session.screen0.toolbar.placement:	BottomCenter
session.screen0.toolbar.widthPercent:	66
session.screen0.workspaceNames:	one,two,three,four
session.screen0.strftimeFormat:	%k:%M
session.screen0.focusNewWindows:	True
session.screen0.focusModel:	ClickToFocus
session.screen0.fullMaximization:	False
session.screen0.edgeSnapThreshold:	0
session.screen0.rowPlacementDirection:	LeftToRight
session.screen0.workspaces:	4
session.screen0.focusLastWindow:	True
session.screen0.colPlacementDirection:	TopToBottom
session.screen0.windowPlacement:	RowSmartPlacement
session.screen0.tab.width:	64
session.screen0.tab.height:	16
session.screen0.showwindowposition: true
session.opaqueMove:	False
session.autoRaiseDelay:	250
**session.menuFile:	~/.fluxbox/menu**
session.cacheLife:	5
session.styleFile:	/usr/local/share/fluxbox/styles/Meta
session.keyFile: ~/.fluxbox/keys
session.colorsPerChannel:	4
session.doubleClickInterval:	250
session.cacheMax:	200
session.imageDither:	True
session.configVersion:	1


As you can see it's suppose to use the menu file in ~/.fluxbox/menu which is my current menu file.

---

