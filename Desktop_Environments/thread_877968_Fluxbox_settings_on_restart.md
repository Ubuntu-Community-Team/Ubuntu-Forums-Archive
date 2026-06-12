---
title: "Fluxbox settings on restart"
date: 2008-08-02
forum: Desktop Environments
---

### Post by Anzan on 2008-08-02
I'm still learning to configure Fluxbox.

I've edited the startup and init files to set a wallpaper and to load nm-applet (amongst other modifications).

This rarely works on first startup but if I log out and in or choose restart in the root menu this is fine.

The wallpaper flashes then vanishes but nm-applet is in the panel. Or the wallpaper loads but nm-applet doesn't. Or neither of them load.

Again, on restart it's all fine.

Does anyone know why this would be?

---

### Post by Diabolis on 2008-08-02
Post your configuration files so we can see how you are doing it.

---

### Post by Anzan on 2008-08-02
All right.

These are just the default init and startup txts with few modifications:

Init:

```
session.screen0.menu.alpha:	254
session.screen0.window.focus.alpha:	255
session.screen0.window.unfocus.alpha:	237
session.screen0.toolbar.widthPercent:	66
session.screen0.toolbar.layer:	Dock
session.screen0.toolbar.alpha:	255
session.screen0.toolbar.autoHide:	false
session.screen0.toolbar.height:	0
session.screen0.toolbar.tools:	workspacename, prevworkspace, nextworkspace, iconbar, systemtray, prevwindow, nextwindow, clock
session.screen0.toolbar.onhead:	0
session.screen0.toolbar.onTop:	False
session.screen0.toolbar.maxOver:	false
session.screen0.toolbar.placement:	BottomCenter
session.screen0.toolbar.visible:	true
session.screen0.overlay.lineWidth:	1
session.screen0.overlay.lineStyle:	LineSolid
session.screen0.overlay.joinStyle:	JoinMiter
session.screen0.overlay.capStyle:	CapNotLast
session.screen0.slit.onTop:	False
session.screen0.slit.layer:	Dock
session.screen0.slit.alpha:	255
session.screen0.slit.onhead:	1
session.screen0.slit.maxOver:	false
session.screen0.slit.direction:	Vertical
session.screen0.slit.placement:	BottomLeft
session.screen0.slit.autoHide:	false
session.screen0.tabs.maxOver:	false
session.screen0.tabs.intitlebar:	true
session.screen0.tab.placement:	TopLeft
session.screen0.tab.width:	64
session.screen0.tab.height:	16
session.screen0.iconbar.wheelMode:	Screen
session.screen0.iconbar.usePixmap:	true
session.screen0.iconbar.iconWidth:	70
session.screen0.iconbar.mode:	Icons
session.screen0.iconbar.iconTextPadding:	10l
session.screen0.iconbar.alignment:	Relative
session.screen0.titlebar.left:	Stick 
session.screen0.titlebar.right:	Minimize Maximize Close 
session.screen0.workspacewarping:	true
session.screen0.focusModel:	ClickFocus
session.screen0.showwindowposition:	true
session.screen0.windowScrollAction:	
session.screen0.edgeSnapThreshold:	0
session.screen0.windowScrollReverse:	false
session.screen0.imageDither:	true
session.screen0.windowMenu:	
session.screen0.opaqueMove:	false
session.screen0.allowRemoteActions:	false
session.screen0.reversewheeling:	false
session.screen0.demandsAttentionTimeout:	500
session.screen0.windowPlacement:	RowSmartPlacement
session.screen0.menuDelay:	0
session.screen0.clickRaises:	true
session.screen0.userFollowModel:	Follow
session.screen0.defaultDeco:	NORMAL
session.screen0.focusNewWindows:	true
session.screen0.strftimeFormat:	%l:%M
session.screen0.fullMaximization:	false
session.screen0.rootCommand:	/usr/bin/fbsetbg -f /home/user/.fluxbox/backgrounds/leak.jpg	
session.screen0.focusLastWindow:	True
session.screen0.tabFocusModel:	ClickToTabFocus
session.screen0.menuDelayClose:	0
session.screen0.rowPlacementDirection:	LeftToRight
session.screen0.colPlacementDirection:	TopToBottom
session.screen0.menuMode:	Delay
session.screen0.decorateTransient:	true
session.screen0.workspaces:	4
session.screen0.desktopwheeling:	true
session.screen0.workspaceNames:	one,two,three,four,
session.screen0.autoRaise:	true
session.screen0.resizeMode:	Bottom
session.screen0.followModel:	Ignore
session.ignoreBorder:	false
session.groupFile:	~/.fluxbox/groups
session.menuFile:	~/.fluxbox/menu
session.tabsAttachArea:	Window
session.doubleClickInterval:	250
session.cacheLife:	5l
session.imageDither:	True
session.tabPadding:	0
session.colorsPerChannel:	4
session.opaqueMove:	False
session.slitlistFile:	~/.fluxbox/slitlist
session.configVersion:	1
session.forcePseudoTransparency:	true
session.styleFile:	/usr/share/fluxbox/styles/BlueNight
session.keyFile:	~/.fluxbox/keys
session.appsFile:	~/.fluxbox/apps
session.styleOverlay:	~/.fluxbox/overlay
session.autoRaiseDelay:	250
session.cacheMax:	200l
session.modKey:	Mod1
```

And startup:

```
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
# fbsetbg -f /home/user/pictures/wallpaper.png

fbsetbg -f /home/user/.fluxbox/backgrounds/leak.jpg
#
# This sets a black background

#/usr/bin/fbsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp "/home/user/.fonts"
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap "/home/user/.Xmodmap"



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &
conky &
gedit &
nm-applet&

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox

# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/user/.fluxbox/log"
```


I had found that the background didn't work at all (except to flash and then vanish) unless I added "/.fluxbox" like so:

fbsetbg -f /home/user/.fluxbox/backgrounds/leak.jpg

Of course "user" replaces the actual username.

---

### Post by Diabolis on 2008-08-02
> nm-applet&

Thats the only problem that I see, should be
```
nm-applet &
```

Just a typo.

You might like this thread: [http://ubuntuforums.org/showthread.php?t=871985](http://ubuntuforums.org/showthread.php?t=871985)

---

### Post by Anzan on 2008-08-02
Great. I'll try that. Thank you.

And about the background? Any thoughts?

---

### Post by Diabolis on 2008-08-02
You have to specify the exact path to the image that you want to use.

This is mine:
```
fbsetbg -f /home/gaston/misDocumentos/imagenes/4359780.png
```

---

### Post by Anzan on 2008-08-02
Yes, I did that:

/usr/bin/fbsetbg -f /home/user/.fluxbox/backgrounds/leak.jpg	

After having especially place the background in that dir so it would be easy to find.

My real question though is:

Why does this stuff work after a restart?

---

### Post by Diabolis on 2008-08-02
Because all the settings are read and loaded to fluxbox when it initializes. Much like when you pass arguments to a command line application.

---

### Post by Anzan on 2008-08-02
Ohhhh....

So I should set Fluxbox to load first and then set the other specifications?

---

### Post by Diabolis on 2008-08-02
nop, leave the startup file as it is. Just edit it following its comments. At the end you'll read a comment that says that fluxbox is the last thing to be executed.

---

### Post by jviscosi on 2008-08-02
Some of the Fluxbox styles (BlueNight is one) specify their own backgrounds, which might be interfering with the wallpaper you're trying to set.  I don't have Fluxbox in front of me at the moment to test it, but you could try commenting out the BlueNight style background entries (or just try a different style) and see if that fixes it.

---

### Post by Diabolis on 2008-08-02
Styles won't interfere because he is setting the wallpaper with the fbsetbg command in the startup file.

Styles would interfere if this was done in the init file.

---

### Post by Anzan on 2008-08-02
I wound up putting it in both init and startup.

I'll try changing the style.

Thanks for your help.

---

### Post by DocYoung on 2008-08-03
Why, may I ask, do you have "gedit &" in your startup?

---

### Post by Anzan on 2008-08-03
I just like to have gedit up and ready. I have the python console and terminal embedded and use it quite extensively.

I think that this problem really does have to do with styles. I'm going to have to look over what is involved with them otherwise further modifications could be buggy.

edit to add:

Oh, I did change the style and (after some restarts) all is well.

---

