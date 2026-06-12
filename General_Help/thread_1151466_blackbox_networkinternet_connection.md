---
title: "blackbox network/internet connection?"
date: 2009-05-06
forum: General Help
---

### Post by iu34 on 2009-05-06
Hi all, I'm trying to test drive blackbox, but I can't use figure out how to connect to the internet with it! I read somewhere that "gksudo network-admin" should work, but it doesn't. (It actually doesn't do anything under gnome either.) Can anyone help?

---

### Post by BslBryan on 2009-05-07
Hello, iu34. :-)
Okay, try this:

```
sudo apt-get install blackbox blackbox-themes
```

And, guess what?  That's all you need to do. :-)  I will provide some more information to give you some more help in customizing it for you, though, :-)

Now, I want you to see if there's a folder called /.blackbox in your home folder.  Make sure to view hidden files.

If so, ignore this next part, but if you don't, then:
```
cd
mkdir .blackbox
```

Now, we need a .blackboxrc file. :-)
```
cd /.blackbox
gedit .blackboxrc
```

Now paste this in:
```
session.styleFile: /usr/share/blackbox/styles/Gray
session.menuFile: /home/**"YOUR_USERNAME"**/.blackbox/menu
session.screen0.slit.placement: CenterRight
session.screen0.slit.direction: Vertical
session.screen0.slit.onTop: False
session.screen0.slit.autoHide: False
session.screen0.toolbar.onTop: False
session.screen0.toolbar.autoHide: False
session.screen0.toolbar.placement: BottomCenter
session.screen0.toolbar.widthPercent: 66
session.screen0.enableToolbar: True
session.screen0.workspaces: 4
session.screen0.workspaceNames: Workspace 1,Workspace 2,Workspace 3,Workspace 4
session.screen0.strftimeFormat: %I:%M %p
session.windowSnapThreshold: 0
session.autoRaiseDelay: 400
session.placementIgnoresShaded: True
session.focusLastWindow: True
session.opaqueMove: True
session.changeWorkspaceWithMouseWheel: True
session.imageDither: OrderedDither
session.windowPlacement: RowSmartPlacement
session.shadeWindowWithMouseWheel: True
session.opaqueResize: True
session.toolbarActionsWithMouseWheel: True
session.rowPlacementDirection: LeftToRight
session.maximumColors: 0
session.disableBindingsWithScrollLock: False
session.fullMaximization: False
session.colPlacementDirection: TopToBottom
session.doubleClickInterval: 250
session.edgeSnapThreshold: 0
session.focusNewWindows: True
session.focusModel: ClickToFocus 
```

Now, for the menu. 

Considering we changed the path of the menu file, we now need to add our own menu.  By the by, **if you don't paste in some sort of menu then nothing will appear with a right click on the desktop. **
```

gedit .blackbox/menu
```

Next is an example of a menu.  Keep in mind that [nop] () is equal to a space.

```
[begin] (b l a c k b o x )
	[exec] (Eterm) {Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x35+13+495 --font-fx none -f lightgrey}
	[nop] ()
	[submenu] (terminals) {terminals}
		[exec] (aterm) {aterm -tr -bg black -fg lightgrey -fn 7x14 -fb 7x14 +vb +sb -geometry 79x32+13+495}
		[exec] (gterm) {gnome-terminal}
		[exec] (kterm) {konsole}
		[exec] (xterm) {xterm -ls}
	[end]
	[submenu] (gnome) {gnome}
		[exec] (nautilus) {nautilus --no-desktop}
		[exec] (gnome-theme-manager) {gnome-theme-manager}
		[exec] (gnome-settings-daemon) {gnome-settings-daemon}
		
	[end]
	[submenu] (audio) {}
		[exec] (xmms) {xmms}
		[exec] (gnome-volume) {gnome-volume-manager}
	[end]
	[submenu] (internet) {}
		[exec] (firefox) {firefox}
		[exec] (gaim) {gaim}
		[exec] (gftp) {gftp}
		[exec] (bluefish) {bluefish}
		[exec] (firestarter) {gksudo /usr/sbin/firestarter}
		[exec] (virus scanner) {aegis-virus-scanner}
	[end]
	[submenu] (graphics) {}
		[exec] (the gimp) {gimp}
	[end]
	[submenu] (office apps) {}
		[exec] (oo.o writer) {ooffice2}
	[end]
	[submenu] (video) {}
		[exec] (gmplayer) {gmplayer}
		[exec] (vlc) {vlc}
		[exec] (xine) {xine}
	[end]
	[submenu] (system monitor) {}
		[exec] (monitor start) {conky}
		[exec] (monitor stop) {killall conky}
	[end]
	[nop] ()
	[workspaces] (workspace list)
	[config] (configuration)
	[nop] ()
	[submenu] (startup) {}
		[exec] (gnome-settings-daemon ) {gnome-settings-daemon &}
		[exec] (conky) {conky &}
		[exec] (Esetroot) {Esetroot .blackbox/backgrounds/Complex_2.jpg}
		[exec] (wmbutton) {wmbutton &}
		[exec] (wmweather) {wmweather -w -s KROC &}
		[exec] (wmcpuload ) {wmcpuload &}
		[exec] (wmclock) {wmclock -12 -led white &}
	[end]
	[nop] ()
	[reconfig] (reconfigure)
	[restart] (restart) {}
	[exit] (exit)
[end]
```

Now, for editing the style. :cool:

```
gksudo gedit /usr/share/blackbox/styles/
```

Now, you can edit it however you'd like. :-)

In order to have a wallpaper, you'll need to install "eterm" to use its "esetroot" utility. 

Add/Replace this command to your current style file for a wallpaper/background:
```
rootCommand: Esetroot /usr/share/blackbox/backgrounds/wallpaper.jpg
```

Log out.  Now, it should be in the gdm!

I hope I've helped.  I can point you in the direction of a couple of other useful programs, if you'd like.  Also, please keep me updated on everything?

Best to you, iu34, and good luck. :-)

---

