---
title: "Another fluxbox question"
date: 2005-08-04
forum: Desktop Environments
---

### Post by astronerd on 2005-08-04
Hi all, I just downloaded fluxbox .9.11 from synaptic and I cant find/ dont know how to make it run.  Basically I just wanted to try it out and see what kind of eye candy and changes I can make to my desktop(thats all it basically does right?  Still not too sure about that part....)  Is there something else I need to add or run?  I am using gnome, hoary.  Is this going to cause more problems than its worth?  Thanks, 
Charles

---

### Post by Digitallysick on 2005-08-04
you should be able to logout and see it in the menu, and select it and log back in , i didn't care for it much, kde rocks

---

### Post by astronerd on 2005-08-04
Ok, so I got it working and when I log into it all I can get from a right click is the options of xterm, restart, and exit.  Nothing else shows up.  and the color they use as default is really light, I can barely read it.  Has anyone else had this problem?  Is there a step by step guide that can explain all these things, and not the one from the website?  I want to give a try cause it looks cool, but if its this much trouble just to set up....
Charles

---

### Post by mattack on 2005-08-04
fluxbox is a lot of work to get a basic desktop system running the way you want it. after installing it, there should be a .fluxbox directory in your home folder. styles (aka themes) can be downloaded from the fluxbox website and put into the styles folder in your .fluxbox directory.
you need an init file to tell fluxbox what to load on startup, what theme to use, etc...
mine looks like this:
```
session.screen0.toolbar.layer:	AboveDock
session.screen0.toolbar.widthPercent:	65
session.screen0.toolbar.autoHide:	false
session.screen0.toolbar.onTop:	true
session.screen0.toolbar.tools:	workspacename, prevworkspace, nextworkspace, iconbar, systemtray, prevwindow, nextwindow, clock
session.screen0.toolbar.alpha:	255
session.screen0.toolbar.onhead:	0
session.screen0.toolbar.height:	0
session.screen0.toolbar.visible:	true
session.screen0.toolbar.maxOver:	false
session.screen0.toolbar.placement:	BottomCenter
session.screen0.slit.alpha:	255
session.screen0.slit.direction:	Vertical
session.screen0.slit.layer:	Desktop
session.screen0.slit.onhead:	0
session.screen0.slit.placement:	TopRight
session.screen0.slit.onTop:	false
session.screen0.slit.maxOver:	true
session.screen0.slit.autoHide:	false
session.screen0.iconbar.wheelMode:	Screen
session.screen0.iconbar.deiconifyMode:	Follow
session.screen0.iconbar.mode:	Workspace
session.screen0.iconbar.iconTextPadding:	10l
session.screen0.iconbar.alignment:	Relative
session.screen0.iconbar.usePixmap:	true
session.screen0.iconbar.iconWidth:	70
session.screen0.tab.width:	0
session.screen0.overlay.lineWidth:	1
session.screen0.overlay.lineStyle:	LineSolid
session.screen0.overlay.joinStyle:	JoinMiter
session.screen0.overlay.capStyle:	CapNotLast
session.screen0.menu.alpha:	160
session.screen0.window.unfocus.alpha:	255
session.screen0.window.focus.alpha:	255
session.screen0.desktopwheeling:	true
session.screen0.focusNewWindows:	true
session.screen0.antialias:	true
session.screen0.focusModel:	ClickToFocus
session.screen0.colPlacementDirection:	TopToBottom
session.screen0.menuDelay:	0
session.screen0.workspaceNames:	one, four, three, two,
session.screen0.imageDither:	false
session.screen0.fullMaximization:	true
session.screen0.workspacewarping:	true
session.screen0.resizeMode:	Bottom
session.screen0.autoRaise:	false
session.screen0.followModel:	Ignore
session.screen0.focusLastWindow:	true
session.screen0.workspaces:	4
session.screen0.windowMenu:	
session.screen0.windowPlacement:	ColSmartPlacement
session.screen0.sloppywindowgrouping:	true
session.screen0.rowPlacementDirection:	LeftToRight
session.screen0.edgeSnapThreshold:	0
session.screen0.clickRaises:	true
session.screen0.decorateTransient:	false
session.screen0.rootCommand:	
session.screen0.menuMode:	Delay
session.screen0.strftimeFormat:	%I:%M %P
session.screen0.opaqueMove:	false
session.screen0.showwindowposition:	true
session.screen0.menuDelayClose:	0
session.titlebar.left:	Stick 
session.titlebar.right:	Minimize Maximize Close 
session.styleFile:	~/.fluxbox/styles/blackbx
session.tabsAttachArea:	Window
session.doubleClickInterval:	250
session.slitlistFile:	~/.fluxbox/slitlist
session.focusTabMinWidth:	0
session.tabs:	true
session.tabPadding:	0
session.autoRaiseDelay:	250
session.useMod1:	true
session.cacheMax:	200l
session.keyFile:	~/.fluxbox/keys
session.cacheLife:	5l
session.ignoreBorder:	false
session.groupFile:	~/.fluxbox/groups
session.forcePseudoTransparency:	false
session.colorsPerChannel:	4
session.menuFile:	~/.fluxbox/menu
session.numLayers:	13
session.appsFile:	~/.fluxbox/apps
``` 

also to get more of a menu, you'll need a menu file in your .fluxbox directory. mine looks like this:
```
#my attempt at a menu for fluxbox
[begin] (Mattack)
    [exec] (Firefox) {firefox}
    [exec] (Thunderbird) {mozilla-thunderbird}
    [exec] (Evolution) {evolution-2.2}
    [exec] (Gaim) {gaim}
    [exec] (LiveJournal) {logjam}
    [exec] (GnuCash) {gnucash}
    [exec] (Gkrellm) {gkrellm -w &}
    [exec] (Term) {xterm}
[submenu] (media) {media}
    [exec] (Madman) {madman}
    [exec] (Beep) {beep-media-player}
    [exec] (iPod) {gtkpod}
    [exec] (Grip) {grip}
    [exec] (EZtag) {easytag}
    [exec] (Cantus3) {cantus3}
    [exec] (Mplayer) {gmplayer}
    [exec] (K3B) {/usr/bin/k3b}  
[end]
[submenu] (net) {net}
    [exec] (Firefox) {firefox}
    [exec] (Thunderbird) {mozilla-thunderbird}
    [exec] (BitTorrent) {/usr/bin/btdownloadgui}
    [exec] (FTP) {gftp %u}
    [exec] (RDP/VNC) {tsclient}
    [exec] (IRC) {xchat}
    [exec] (Gaim) {gaim}
    [exec] (LiveJournal) {logjam}
[end]
[submenu] (edit) {edit}
    [exec] (Gedit) {gedit}
    [exec] (Word) {/usr/bin/oowriter %U}
    [exec] (Spreadsheet) {/usr/bin/oocalc %U}
    [exec] (Draw) {/usr/bin/oodraw %U}
    [exec] (Gimp) {gimp-remote-2.2 %U}
[end]
[submenu] (accessories) {accessories}
    [exec] (Gedit) {gedit}
    [exec] (Character Map) {gucharmap}
    [exec] (Calculator) {gcalctool}
[end]
[submenu] (admin) {admin}
    [exec] (Synaptic) {gksudo /usr/sbin/synaptic}
    [exec] (Update) {gksudo /usr/bin/update-manager}
    [exec] (Fluxbare) {fluxbare}
    [config] (Configure) 
[end]    
    [restart] (Restart)
    [exit] (Exit)
[end]
``` 

there are other files that you may want or need depending on how you want to configure your fluxbox setup... i gave up because it was too much work. i like tinkering, don't get me wrong, but i like things to be fairly usable right out of the box.
i hope this helps...

---

### Post by astronerd on 2005-08-04
So basically I have to conifigure anything I want in code, right?  I have to manually add it into the .int file and such to configure and put a new option or something in?  There has to be an easier way, right?  Is there something else I can use to besides fluxbox then?  I just want to customize my desktop from the standard gnome stuff and have some nice eyecandy.  Tried gdesklets, and they ate too much memory.  Plus I wanna change the task bar etc.  but not if its gonna take forever like it seems to with fluxbox.  Any suggestions?

---

### Post by danns on 2005-08-05
Fluxbox is not that hard to configure.  It may look daunting at first, but read the docs and you will find it is quite easy.  The documentation on their website is pretty good:    [http://www.fluxbox.org/](http://www.fluxbox.org) 

there is a utility that will help you with this:  fluxconf, you can find it in synaptic.

---

