---
title: "Fluxbox Dock Icon Proble"
date: 2008-03-21
forum: Desktop Environments
---

### Post by solarwind on 2008-03-21
Hey all, I just installed Fluxbox and I love it. One problem though: the icons in my dock look messed up and ugly. How do I fix this? Or, how do I get rid of icons in the Dock altogether? Here's a screenshot:

[IMG]http://img166.imageshack.us/img166/6815/200803211603081680x1050qi1.png[/IMG]

---

### Post by canistra on 2008-03-21
show us the output of the ~/.fluxbox/init file

---

### Post by solarwind on 2008-03-21
```
vg@vg-desktop:~$ cat /home/vg/.fluxbox/init 
session.screen0.tabs.maxOver:   false
session.screen0.tabs.intitlebar:        true
session.screen0.tab.placement:  TopLeft
session.screen0.tab.width:      64
session.screen0.tab.height:     16
session.screen0.iconbar.wheelMode:      Screen
session.screen0.iconbar.iconWidth:      70
session.screen0.iconbar.usePixmap:      true
session.screen0.iconbar.mode:   Workspace
session.screen0.iconbar.alignment:      Relative
session.screen0.iconbar.iconTextPadding:        10l
session.screen0.titlebar.left:  Stick 
session.screen0.titlebar.right: Minimize Maximize Close 
session.screen0.slit.onhead:    0
session.screen0.slit.autoHide:  false
session.screen0.slit.direction: Vertical
session.screen0.slit.layer:     Dock
session.screen0.slit.placement: BottomRight
session.screen0.slit.onTop:     False
session.screen0.slit.alpha:     255
session.screen0.slit.maxOver:   false
session.screen0.toolbar.visible:        true
session.screen0.toolbar.onhead: 0
session.screen0.toolbar.maxOver:        false
session.screen0.toolbar.alpha:  255
session.screen0.toolbar.tools:  workspacename, prevworkspace, nextworkspace, iconbar, systemtray, prevwindow, nextwindow, clock
session.screen0.toolbar.placement:      BottomCenter
session.screen0.toolbar.layer:  Dock
session.screen0.toolbar.widthPercent:   66
session.screen0.toolbar.autoHide:       false
session.screen0.toolbar.onTop:  False
session.screen0.toolbar.height: 0
session.screen0.window.focus.alpha:     255
session.screen0.window.unfocus.alpha:   255
session.screen0.menu.alpha:     255
session.screen0.overlay.lineWidth:      1
session.screen0.overlay.lineStyle:      LineSolid
session.screen0.overlay.joinStyle:      JoinMiter
session.screen0.overlay.capStyle:       CapNotLast
session.screen0.clickRaises:    true
session.screen0.reversewheeling:        false
session.screen0.focusLastWindow:        True
session.screen0.colPlacementDirection:  TopToBottom
session.screen0.focusModel:     ClickFocus
session.screen0.tabFocusModel:  ClickToTabFocus
session.screen0.allowRemoteActions:     false
session.screen0.windowMenu:
session.screen0.menuMode:       Delay
session.screen0.fullMaximization:       false
session.screen0.decorateTransient:      true
session.screen0.menuDelay:      0
session.screen0.windowPlacement:        RowSmartPlacement
session.screen0.edgeSnapThreshold:      0
session.screen0.defaultDeco:    NORMAL
session.screen0.windowScrollAction:
session.screen0.showwindowposition:     true
session.screen0.autoRaise:      true
session.screen0.opaqueMove:     false
session.screen0.followModel:    Ignore
session.screen0.rootCommand:
session.screen0.rowPlacementDirection:  LeftToRight
session.screen0.workspacewarping:       true
session.screen0.menuDelayClose: 0
session.screen0.resizeMode:     Bottom
session.screen0.imageDither:    false
session.screen0.workspaceNames: one,two,three,four,
session.screen0.userFollowModel:        Follow
session.screen0.desktopwheeling:        true
session.screen0.workspaces:     4
session.screen0.strftimeFormat: %k:%M
session.screen0.windowScrollReverse:    false
session.screen0.focusNewWindows:        true
session.autoRaiseDelay: 250
session.opaqueMove:     False
session.keyFile:        ~/.fluxbox/keys
session.tabsAttachArea: Window
session.groupFile:      ~/.fluxbox/groups
session.ignoreBorder:   false
session.colorsPerChannel:       4
session.configVersion:  1
session.forcePseudoTransparency:        false
session.modKey: Mod1
session.menuFile:       ~/.fluxbox/menu
session.imageDither:    True
session.doubleClickInterval:    250
session.cacheLife:      5l
session.slitlistFile:   ~/.fluxbox/slitlist
session.styleOverlay:   ~/.fluxbox/overlay
session.cacheMax:       200l
session.appsFile:       ~/.fluxbox/apps
session.tabPadding:     0
session.styleFile:      /home/vg/.fluxbox/styles/Dyne

```

---

### Post by canistra on 2008-03-21
change this line:

```
session.screen0.iconbar.usePixmap:      true
```

to

```
session.screen0.iconbar.usePixmap:      false
```

then restart fluxbox

---

### Post by solarwind on 2008-03-21
> **canistra said:**
> change this line:

```
session.screen0.iconbar.usePixmap:      true
```

to

```
session.screen0.iconbar.usePixmap:      false
```

then restart fluxbox

Solved the problem. Very helpful. Thanks a lot!

Also, do you know how to change the width of the taskbar?

---

### Post by RedSquirrel on 2008-03-21
> **solarwind said:**
> Solved the problem. Very helpful. Thanks a lot!

Also, do you know how to change the width of the taskbar?
If you want your icons to look better, you could compile your own fluxbox. Instructions for that can be found in the tutorial link in my signature. (I understand that many people are not up for compiling, but I just thought I'd mention it. ;))


Toolbar width: just right-click on the toolbar and right-click on "toolbar width percent" to increase, left-click to decrease.


The height of the toolbar is set in the style's configuration file. If you are installing new styles, install them to ~/.fluxbox/styles. If you want to modify one of the styles that is installed with the fluxbox package, simply copy it from /usr/share/fluxbox/styles to ~/.fluxbox/styles.

```
toolbar.height: 25
```

See:

```
man fluxstyle
```

---

### Post by fela on 2008-03-22
> **solarwind said:**
> Hey all, I just installed Fluxbox and I love it.

is that as simple as sudo apt-get install fluxbox? or is there a metapackage that depends on all other fluxbox stuff, like kubuntu-desktop?

---

### Post by solarwind on 2008-03-22
> **fela said:**
> is that as simple as sudo apt-get install fluxbox? or is there a metapackage that depends on all other fluxbox stuff, like kubuntu-desktop?

It's pretty much as simple as that. I used this guide as a reference: [https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox)

Also, use menu maker to generate your fluxbox menu. I find it works very well.

---

### Post by fela on 2008-03-22
thanks, i might try fluxbox myself...:D

---

### Post by solarwind on 2008-03-22
> **fela said:**
> thanks, i might try fluxbox myself...:D

It's very nice. You need to get used to it, but I'm sure you'll love it.

---

