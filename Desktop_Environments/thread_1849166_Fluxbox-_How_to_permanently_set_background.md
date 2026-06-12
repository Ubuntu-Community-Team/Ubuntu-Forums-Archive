---
title: "Fluxbox- How to permanently set background?"
date: 2011-09-23
forum: Desktop Environments
---

### Post by keelx on 2011-09-23
I'm just fine with having one background per style. However, I can't get it to stay at my background. It always shows my background for about a second, and then switches to the default (and rather ugly) background for whatever style I'm using. I've tried everything I could find.
Here is my init file:
```

session.screen0.slit.placement:	RightBottom
session.screen0.slit.alpha:	255
session.screen0.slit.layer:	Dock
session.screen0.slit.autoHide:	false
session.screen0.slit.acceptKdeDockapps:	true
session.screen0.slit.maxOver:	false
session.screen0.slit.onhead:	0
session.screen0.clientMenu.usePixmap:	true
session.screen0.iconbar.mode:	{static groups} (workspace)
session.screen0.iconbar.alignment:	Relative
session.screen0.iconbar.iconTextPadding:	10
session.screen0.iconbar.iconWidth:	128
session.screen0.iconbar.usePixmap:	true
session.screen0.titlebar.left:	Stick 
session.screen0.titlebar.right:	Minimize Maximize Close 
session.screen0.tab.placement:	TopLeft
session.screen0.tab.width:	64
session.screen0.tabs.usePixmap:	true
session.screen0.tabs.maxOver:	false
session.screen0.tabs.intitlebar:	true
session.screen0.toolbar.autoHide:	false
session.screen0.toolbar.alpha:	255
session.screen0.toolbar.tools:	prevworkspace, workspacename, nextworkspace, clock, prevwindow, nextwindow, iconbar, systemtray
session.screen0.toolbar.height:	0
session.screen0.toolbar.onhead:	1
session.screen0.toolbar.maxOver:	false
session.screen0.toolbar.placement:	BottomCenter
session.screen0.toolbar.layer:	Dock
session.screen0.toolbar.visible:	true
session.screen0.toolbar.widthPercent:	100
session.screen0.window.focus.alpha:	0
session.screen0.window.unfocus.alpha:	255
session.screen0.menu.alpha:	131
session.screen0.opaqueMove:	true
session.screen0.tooltipDelay:	500
session.screen0.focusNewWindows:	true
session.screen0.showwindowposition:	false
session.screen0.maxDisableResize:	false
session.screen0.menuDelay:	200
session.screen0.noFocusWhileTypingDelay:	0
session.screen0.edgeSnapThreshold:	10
session.screen0.allowRemoteActions:	false
session.screen0.autoRaise:	true
session.screen0.windowMenu:	/home/hoodwink/.fluxbox/windowmenu
session.screen0.maxDisableMove:	false
session.screen0.strftimeFormat:	%I:%M:%S
session.screen0.workspaces:	4
session.screen0.defaultDeco:	NORMAL
session.screen0.maxIgnoreIncrement:	true
session.screen0.fullMaximization:	false
session.screen0.windowPlacement:	RowMinOverlapPlacement
session.screen0.workspacewarping:	true
session.screen0.focusModel:	ClickFocus
session.screen0.colPlacementDirection:	TopToBottom
session.screen0.rowPlacementDirection:	LeftToRight
session.screen0.workspaceNames:	Workspace 1,Workspace 2,Workspace 3,Background Processes,
session.screen0.tabFocusModel:	ClickToTabFocus
session.screen0.clickRaises:	true
session.tabsAttachArea:	Window
session.menuFile:	~/.fluxbox/menu
session.slitlistFile:	/home/hoodwink/.fluxbox/slitlist
session.doubleClickInterval:	250
session.cacheLife:	5
session.configVersion:	13
session.tabPadding:	0
session.ignoreBorder:	false[HTML][/HTML]
session.autoRaiseDelay:	250
session.colorsPerChannel:	4
session.styleFile:	/usr/share/fluxbox/styles/Ubuntu-dark
session.cacheMax:	200
session.appsFile:	/home/hoodwink/.fluxbox/apps
session.keyFile:	~/.fluxbox/keys
session.styleOverlay:	/home/hoodwink/.fluxbox/overlay
session.forcePseudoTransparency:	false
**session.screen0.rootCommand: fbsetbg -f ~/Pictures/Ubuntu_wallpaper_edit.png**

```

My overlay file:
```

! The following line will prevent styles from setting the background.
background: none
background: centered
background.pixmap ~/Pictures/Ubuntu_wallpaper_edit.png

```

And my startup file:
```

#!/bin/sh
#
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# Change your keymap:
xmodmap "/home/hoodwink/.Xmodmap"

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

nm-applet &
**fbsetbg ~/Pictures/Ubuntu_wallpaper_edit.png &**

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec fluxbox
# or if you want to keep a log:
# exec fluxbox -log "/home/hoodwink/.fluxbox/log"

```

Even having it continuously set and reset the background to my image won't work.

What can I do to make this work? This is getting rather annoying...
](*,)

---

### Post by keelx on 2011-09-24
Come on, this problem surely must have been solved before.

---

### Post by Krytarik on 2011-09-24
> **keelx said:**
> Come on, this problem surely must have been solved before.
Please be patient! As there aren't many users using Fluxbox in the first place, it seems. ;-)
And 'bumping' threads is generally only allowed after at least 24 hours.

Incidentially, I have Fluxbox installed parallelly to Gnome and XFCE. But as it doesn't seem to work out too great, I didn't bother too much with it so far.

Hope someone Fluxbox-literate crosses this place!

---

### Post by keelx on 2011-09-24
> **Krytarik said:**
> Please be patient! As there aren't many users using Fluxbox in the first place, it seems. ;-)
And 'bumping' threads is generally only allowed after at least 24 hours.

Incidentially, I have Fluxbox installed parallelly to Gnome and XFCE. But as it doesn't seem to work out too great, I didn't bother too much with it so far.

Hope someone Fluxbox-literate crosses this place!

Sorry, I posted this *late* last night (American Central Time), and I had slept, and it felt like 24 hours. But now  realize it was only a few hours. I too hope someone comes along, because I really like this window manager. But it doesn't seem to want me to configure it.

---

### Post by boydrice on 2011-09-24
I usually just set the background in my .xinitrc file.  If you set the background in a terminal by running fbsetbg -f ~/path/to/wallpaer and then add fbsetbg -l to your fluxbox startup file does your background not save for the next session?

---

### Post by keelx on 2011-09-24
> **boydrice said:**
> I usually just set the background in my .xinitrc file.  If you set the background in a terminal by running fbsetbg -f ~/path/to/wallpaer and then add fbsetbg -l to your fluxbox startup file does your background not save for the next session?

Thank you very much. This works. Previously, I had fbsetbd ~/path/to/wallpaper in the startup file, and it would startup with my wallpaper, but then immediately switch to the default background.

---

### Post by boydrice on 2011-09-24
Cool, glad I could help.  I love fluxbox, it is an awesome wm.  Below are some invaluable links on more fluxbox info.  Have a good one.

[http://en.gentoo-wiki.com/wiki/Fluxbox]("http://en.gentoo-wiki.com/wiki/Fluxbox")

[https://wiki.archlinux.org/index.php/Fluxbox]("https://wiki.archlinux.org/index.php/Fluxbox")

[http://fluxbox-wiki.org/index.php?title=Fluxbox-wiki]("http://fluxbox-wiki.org/index.php?title=Fluxbox-wiki")

---

