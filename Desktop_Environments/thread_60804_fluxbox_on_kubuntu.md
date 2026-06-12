---
title: "fluxbox on kubuntu"
date: 2005-08-29
forum: Desktop Environments
---

### Post by ippiraman on 2005-08-29
I installed fluxbox including all suggested packages via apt-get install. The only problem was ~/.fluxbox/init file is empty. I tried looking in /usr/share/fluxbox but found only the default styles bundled with fluxbox. So I downloaded the source from [www.fluxbox.org](www.fluxbox.org), extacted and copied the init file to ~/.fluxbox. After setting the style I want, I logged in using fluxbox session, but I only get teeny weeny menu (I couldn't even read the contents).

Any hints? I tried googling for some sample init files and dug up docs from [www.fluxbox.org](www.fluxbox.org) but I couldn't find any help on init file configuration settings.

Thanks.

---

### Post by bizzaroMike on 2005-08-29
Download the source tarball and untar it.  Check inside there for the stuff it puts into /etc or into /usr/share.  When I played with FB a few months ago, there were sample config files with the source.  But also online at fluxbox.org.  How strange that they're gone.

---

### Post by ippiraman on 2005-08-31
I did download the source tarball and the default init file doesn't work either. Anyway I already solved the problem...

I booted FreesBIE and copied the init file to a USB thumbdrive then dropped it in ~/.fluxbox. Worked like a charm. Anyway if anyone needs it just copy the one below:

[INDENT]<snip>

session.screen0.toolbar.maxOver:	false
session.screen0.toolbar.widthPercent:	68
session.screen0.toolbar.placement:	BottomCenter
session.screen0.toolbar.alpha:	255
session.screen0.toolbar.visible:	true
session.screen0.toolbar.onTop:	false
session.screen0.toolbar.height:	0
session.screen0.toolbar.autoHide:	false
session.screen0.toolbar.tools:	workspacename, prevworkspace, nextworkspace, iconbar, systemtray, prevwindow, nextwindow, clock
session.screen0.toolbar.onhead:	0
session.screen0.toolbar.layer:	Desktop
session.screen0.slit.maxOver:	false
session.screen0.slit.onTop:	false
session.screen0.slit.autoHide:	false
session.screen0.slit.onhead:	0
session.screen0.slit.placement:	BottomRight
session.screen0.slit.alpha:	191
session.screen0.slit.direction:	Vertical
session.screen0.slit.layer:	Dock
session.screen0.iconbar.iconWidth:	70
session.screen0.iconbar.alignment:	Relative
session.screen0.iconbar.iconTextPadding:	10l
session.screen0.iconbar.deiconifyMode:	Follow
session.screen0.iconbar.wheelMode:	Screen
session.screen0.iconbar.usePixmap:	true
session.screen0.iconbar.mode:	Workspace
session.screen0.overlay.lineWidth:	1
session.screen0.overlay.lineStyle:	LineSolid
session.screen0.overlay.joinStyle:	JoinMiter
session.screen0.overlay.capStyle:	CapNotLast
session.screen0.tab.rotatevertical:	True
session.screen0.tab.alignment:	Left
session.screen0.tab.height:	32
session.screen0.tab.placement:	Top
session.screen0.tab.width:	64
session.screen0.menu.alpha:	255
session.screen0.window.focus.alpha:	255
session.screen0.window.unfocus.alpha:	255
session.screen0.menuAlpha:	191
session.screen0.clickRaises:	true
session.screen0.resizeMode:	Bottom
session.screen0.workspaces:	2
session.screen0.fullMaximization:	false
session.screen0.rootCommand:	
session.screen0.showwindowposition:	true
session.screen0.opaqueMove:	true
session.screen0.workspacewarping:	true
session.screen0.sloppywindowgrouping:	true
session.screen0.antialias:	true
session.screen0.workspaceNames:	one,two,
session.screen0.followModel:	Ignore
session.screen0.focusLastWindow:	true
session.screen0.windowMenu:	
session.screen0.focusModel:	ClickToFocus
session.screen0.strftimeFormat:	%k:%M
session.screen0.menuDelay:	0
session.screen0.edgeSnapThreshold:	0
session.screen0.autoRaise:	false
session.screen0.imageDither:	false
session.screen0.windowPlacement:	RowSmartPlacement
session.screen0.menuMode:	Delay
session.screen0.menuDelayClose:	0
session.screen0.decorateTransient:	true
session.screen0.rowPlacementDirection:	LeftToRight
session.screen0.focusNewWindows:	true
session.screen0.desktopwheeling:	true
session.screen0.colPlacementDirection:	TopToBottom
session.titlebar.left:	Stick 
session.titlebar.right:	Minimize Maximize Close 
session.iconbar:	true
session.keyFile:	~/.fluxbox/keys
session.cacheLife:	5l
session.appsFile:	~/.fluxbox/apps
session.slitlistFile:	
session.numLayers:	13
session.opaqueMove:	False
session.focusTabMinWidth:	0
session.tabs:	true
session.menuFile:	~/.fluxbox/menu
session.forcePseudoTransparency:	false
session.doubleClickInterval:	250
session.styleFile:	/usr/share/fluxbox/Artwiz
session.groupFile:	
session.colorsPerChannel:	4
session.autoRaiseDelay:	250
session.imageDither:	True
session.ignoreBorder:	false
session.tabsAttachArea:	Window
session.updateDelayTime:	0
session.cacheMax:	200l
session.useMod1:	true
session.tabPadding:	0

</snip>[/INDENT]

HTH

---

