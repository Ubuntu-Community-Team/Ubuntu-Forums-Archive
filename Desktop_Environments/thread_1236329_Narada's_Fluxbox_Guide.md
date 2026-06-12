---
title: "Narada's Fluxbox Guide"
date: 2009-08-10
forum: Desktop Environments
---

### Post by Narada on 2009-08-10
**Narada's Fluxbox Guide**

What is the point of this guide? To provide you with a quick walkthrough and introduction to a functional Fluxbox setup. 

What is Fluxbox, you ask? Fluxbox is a speedy, lightweight, highly configurable window manager for X. Like its Blackbox parent, Fluxbox uses plaintext configuration files to control and tweak just about any part of the window manager itself. Fluxbox is popular for its simplicity, low memory footprint, and of course, general sex-appeal. You can find out more at [http://www.fluxbox.org/](http://www.fluxbox.org/).


**My Setup**

[[IMG]http://img197.imageshack.us/img197/1550/lappy0809.th.jpg[/IMG]](http://img197.imageshack.us/my.php?image=lappy0809.jpg)

The above screenshot is of my current Fluxbox desktop. We will be looking at each aspect of this; The toolbar, the menu, the windows, applications, and decorations. Configuration files will also be demonstrated in order to provide better explanations.


**The Menu**
Because Fluxbox lacks a 'Start' menu commonplace in many window managers, having a functional menu is critical. Instead of a button on the toolbar, the menu in Fluxbox is opened by right-clicking anywhere on the desktop. Most of the time people use an automatically generated menu, but on occasion someone may need to do some fine tuning. All options on said menu can be edited using the configuration file found at ~/.fluxbox/menu:
```
[begin] (Fluxbox) {} 
    [exec] (aterm) {aterm} 
    [exec] (thunar) {thunar} 
    [exec] (firefox) {LD_PRELOAD=/usr/lib/libGL.so.1 firefox} 
    [exec] (Run) {fbrun } 
    [submenu] (Net) {} 
        [exec] (deluge) {deluge} 
        [exec] (firefox) {firefox} 
        [exec] (opera) {opera} 
        [exec] (pidgin) {pidgin} 
        [submenu] (Tools) {} 
            [exec] (nmap) {aterm -e nmap} 
            [exec] (putty) {putty} 
            [exec] (wireshark) {sudo wireshark} 
        [end]
    [end]
    [submenu] (Editors) {} 
        [exec] (apophysis) {wine ~/.wine/drive_c/apo/Apophysis208beta2.exe} 
        [exec] (emacs) {emacs}
        [exec] (evince) {evince} 
        [exec] (mousepad) {mousepad} 
        [exec] (openoffice) {soffice} 
        [exec] (xaos) {xaos} 
    [end]
    [submenu] (Multimedia) {} 
        [exec] (consonance) {consonance}
        [exec] (exaile) {exaile} 
        [exec] (gimp) {gimp} 
        [exec] (idjc) {idjc}
        [exec] (mplayer) {mplayer} 
        [exec] (vlc) {vlc} 
    [end]
    [submenu] (X-utils) {} 
        [exec] (nvidia-settings) {nvidia-settings} 
        [exec] (gtkpod) {gtkpod}
        [exec] (k3b) {k3b} 
        [exec] (VirtualBox) {VirtualBox}
        [exec] (xcalc) {xcalc} 
        [exec] (Reload .Xdefaults) {xrdb -load /home/narada/.Xdefaults} 
    [end]
    [submenu] (fluxbox menu) {} 
        [config] (Configure) {} 
        [submenu] (System Styles) {Choose a style...} 
            [stylesdir] (/usr/share/fluxbox/styles) {} 
        [end]
        [submenu] (User Styles) {Choose a style...} 
            [stylesdir] (~/.fluxbox/styles) {} 
        [end]
        [submenu] (Wallpapers) {} 
            [wallpapers] (~/.fluxbox/backgrounds) {} 
        [end]
        [workspaces] (Workspace List) {} 
        [submenu] (Tools) {} 
            [exec] (fluxconf) {fluxconf} 
            [exec] (fluxkeys) {fluxkeys} 
            [exec] (fluxmenu) {fluxmenu} 
            [exec] (Window name) {xprop WM_CLASS|cut -d \" -f 2|xmessage -file - -center} 
            [exec] (Run) {fbrun } 
            [exec] (Regen Menu) {/usr/bin/fluxbox-generate_menu } 
        [end]
        [commanddialog] (Fluxbox Command) {} 
        [reconfig] (Reload config) {} 
        [restart] (Restart) {} 
        [exec] (About) {(fluxbox -v; fluxbox -info | sed 1d) 2> /dev/null | xmessage -file - -center} 
        [separator] () {} 
        [exec] (Suspend) {sudo pm-suspend} 
        [exec] (Hibernate) {sudo pm-hibernate}
        [exit] (Exit) {}
    [end]
[end]
```
The above is my ~/.fluxbox/menu. The syntax is actually quite simple. First, you must use [begin] to tell the file the menu configuration is starting. Once you have begun the menu you're free to use other options, like [exec].

[exec] is used to execute a program. Directly following [exec] is the (program name) you want to show up in the menu. Next comes the actual {command} used to execute said program. Say we wanted to run a program labeled "foo" that is traditionally started by using "bar" from a terminal:
```
[exec] (foo) {bar}
```
Simple, right?

As you may have noticed in the screenshot, it is possible to have submenus. This is done by designating a [submenu]:
```
[submenu] (Menu name) {}
```
The {} is blank in this case because we have no use for it - We just want to expand another menu. Following this [submenu] entry you may simply list things like normal. It is also important to note that once you are done listing the contents of your submenu you need to let Fluxbox know you're done by using a [end].  Let's look at our example again:
```
[submenu] (Submenu 1) {}
    [exec] (foo) {bar}
[end]
```

The menu also has some special cases when it comes to options. One can designate a wallpaper directory, Fluxbox styles/theme directory, make an entry to control various elements of the window manager itself, among other things. I will provide a few examples;

To create a wallpaper selecting menu entry:
```
[submenu] (Wallpapers) {}
    [wallpapers] (~/.fluxbox/backgrounds) {}
[end]
```
To create a styles/themes menu entry:
```
[submenu] (User Styles) {}
    [stylesdir] (~/.fluxbox/styles) {}
[end]
```
To create a "Run" dialog:
```
[exec] (Run) {fbrun }
```
To create a separator in your menu:
```
[separator] () {}
```
To reload your Fluxbox configuration files (instead of restarting X):
```
[reconfig] (Reload config)
```
There are many other special instances, all of which can be found here: [http://fluxbox-wiki.org/index.php?title=Editing_the_menu](http://fluxbox-wiki.org/index.php?title=Editing_the_menu)


**The init File**

The init file is located at ~/.fluxbox/init. It contains the configuration for the framework of the Fluxbox session itself. This one I'm not going to go into detail on as I could write a paper on it solely, so I'll just post mine and provide you with a link should you wish to learn more information:
```
session.screen0.iconbar.mode:	{static groups} (workspace)
session.screen0.iconbar.iconTextPadding:	10l
session.screen0.iconbar.alignment:	Relative
session.screen0.iconbar.wheelMode:	Screen
session.screen0.iconbar.usePixmap:	true
session.screen0.iconbar.iconWidth:	70
session.screen0.clientMenu.usePixmap:	true
session.screen0.slit.layer:	Desktop
session.screen0.slit.alpha:	255
session.screen0.slit.placement:	RightBottom
session.screen0.slit.onTop:	false
session.screen0.slit.direction:	Vertical
session.screen0.slit.acceptKdeDockapps:	true
session.screen0.slit.maxOver:	false
session.screen0.slit.autoHide:	false
session.screen0.slit.onhead:	0
session.screen0.menu.alpha:	255
session.screen0.tabs.maxOver:	false
session.screen0.tabs.intitlebar:	true
session.screen0.tabs.usePixmap:	false
session.screen0.overlay.lineWidth:	1
session.screen0.overlay.lineStyle:	LineSolid
session.screen0.overlay.joinStyle:	JoinMiter
session.screen0.overlay.capStyle:	CapNotLast
session.screen0.tab.placement:	TopLeft
session.screen0.tab.width:	64
session.screen0.tab.height:	16
session.screen0.titlebar.left:	Stick 
session.screen0.titlebar.right:	Minimize Maximize Close 
session.screen0.window.focus.alpha:	255
session.screen0.window.unfocus.alpha:	200
session.screen0.toolbar.alpha:	255
session.screen0.toolbar.visible:	true
session.screen0.toolbar.height:	0
session.screen0.toolbar.layer:	Normal
session.screen0.toolbar.placement:	BottomCenter
session.screen0.toolbar.onTop:	false
session.screen0.toolbar.widthPercent:	70
session.screen0.toolbar.tools:	workspacename, prevworkspace, nextworkspace, iconbar, systemtray, prevwindow, nextwindow, clock
session.screen0.toolbar.onhead:	2
session.screen0.toolbar.maxOver:	false
session.screen0.toolbar.autoHide:	false
session.screen0.focusLastWindow:	True
session.screen0.focusNewWindows:	true
session.screen0.rowPlacementDirection:	LeftToRight
session.screen0.strftimeFormat:	%l:%M
session.screen0.imageDither:	false
session.screen0.followModel:	Ignore
session.screen0.fullMaximization:	false
session.screen0.decorateTransient:	true
session.screen0.rootCommand:	fbsetbg -l
session.screen0.resizeMode:	Bottom
session.screen0.tabFocusModel:	ClickToTabFocus
session.screen0.demandsAttentionTimeout:	500
session.screen0.desktopwheeling:	true
session.screen0.opaqueMove:	true
session.screen0.menuDelay:	0
session.screen0.defaultDeco:	NORMAL
session.screen0.maxIgnoreIncrement:	true
session.screen0.maxDisableResize:	false
session.screen0.userFollowModel:	Follow
session.screen0.workspacewarping:	true
session.screen0.windowMenu:	
session.screen0.focusModel:	ClickFocus
session.screen0.windowScrollReverse:	false
session.screen0.edgeSnapThreshold:	0
session.screen0.colPlacementDirection:	TopToBottom
session.screen0.noFocusWhileTypingDelay:	0l
session.screen0.reversewheeling:	false
session.screen0.workspaceNames:	one,two,three,four,
session.screen0.windowPlacement:	RowSmartPlacement
session.screen0.showwindowposition:	true
session.screen0.autoRaise:	true
session.screen0.menuDelayClose:	0
session.screen0.windowScrollAction:	
session.screen0.maxDisableMove:	false
session.screen0.workspaces:	3
session.screen0.menuMode:	Delay
session.screen0.tooltipDelay:	500
session.screen0.clickRaises:	true
session.screen0.allowRemoteActions:	false
session.cacheLife:	5l
session.doubleClickInterval:	250
session.slitlistFile:	~/.fluxbox/slitlist
session.menuFile:	~/.fluxbox/menu
session.imageDither:	True
session.tabPadding:	0
session.colorsPerChannel:	4
session.ignoreBorder:	false
session.groupFile:	~/.fluxbox/groups
session.configVersion:	10
session.cacheMax:	200l
session.styleFile:	/home/narada/.fluxbox/styles/temp.cfg
session.styleOverlay:	~/.fluxbox/overlay
session.forcePseudoTransparency:	false
session.opaqueMove:	False
session.keyFile:	~/.fluxbox/keys
session.modKey:	Mod1
session.appsFile:	~/.fluxbox/apps
session.tabsAttachArea:	Window
session.autoRaiseDelay:	250
```
More info: [http://fluxbox-wiki.org/index.php?title=Editing_the_init_file](http://fluxbox-wiki.org/index.php?title=Editing_the_init_file)


**The Startup File**

The startup file is located at ~/.fluxbox/startup. It contains configuration details for what applications are to be started automatically when Fluxbox is launched. It is, in essence, a duplicate xinitrc file. Personally, I use 'startx' and .xinitrc to run my startup programs and ONLY have the line to execute Fluxbox in my startup file:
```
# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/narada/.fluxbox/log"
```
My .xinitrc:
```
#!/bin/sh
#~/.xinitrc
#
setxkbmap -option terminate:ctrl_alt_bksp
sysresources=/etc/X11/xinit/.Xresources
sysmodmap=/etc/X11/xinit/.Xmodmap

# merge in defaults and keymaps
if [ -f $sysresources ]; then
    xrdb -merge $sysresources
fi
if [ -f $sysmodmap ]; then
    xmodmap $sysmodmap
fi

# D-bus
if which dbus-launch >/dev/null && test -z "$DBUS_SESSION_BUS_ADDRESS"; then
       eval `dbus-launch --sh-syntax --exit-with-session`
fi

conky -dq &
aterm1 &
aterm2 &
volwheel &
exec startfluxbox
```


**The Apps File**

The apps file is located in ~/.fluxbox/apps. It contains configuration data for any specific program that you wanted to save particular settings for. Mine is below:
```
[app] (name=aterm1) (class=XTerm)
  [Dimensions]	{567 514}
  [Deco]	{NONE}
  [IconHidden]	{yes}
  [Layer]	{10}
[end]
[app] (name=aterm2) (class=XTerm)
  [Dimensions]	{567 514}
  [Position]	(UPPERLEFT)	{0 508}
  [Deco]	{NONE}
  [IconHidden]	{yes}
  [Layer]	{12}
[end]
[app] (name=explorer.exe) (class=Wine)
[end]
[app] (name=Navigator) (class=Shiretoko) (role=browser)
  [Position]	(UPPERLEFT)	{567 0}
[end]
[app] (name=emacs) (class=Emacs)
  [Dimensions]	{1000 900}
  [Alpha]	{150 200}
[end]

```
Using the apps file you have an immense amount of flexibility regarding applications. You can literally configure every option that you normally have to configure when the application is already running (by right-clicking its respective title bar). As a note, the syntax with [Dimensions/Position] is {X-coordinate Y-coordinate} and the syntax for [Alpha] (transparency) is {when-window-is-focused when-window-is-unfocused}. More information on the apps file can be found here: [http://fluxbox-wiki.org/index.php?title=Editing_the_apps_file](http://fluxbox-wiki.org/index.php?title=Editing_the_apps_file)


**The Keys File**

The keys file is a particularly awesome and simple part of Fluxbox. It is located in ~/.fluxbox/keys and holds all information regarding hotkeys and button clicks in Fluxbox. Example:
```
!mouse actions added by fluxbox-update_configs
OnTitlebar Mouse2 :StartTabbing

!mouse actions added by fluxbox-update_configs
OnTitlebar Double Mouse1 :Shade
OnTitlebar Mouse3 :WindowMenu

!mouse actions added by fluxbox-update_configs
OnWindow Mod1 Mouse1 :MacroCmd {Raise} {Focus} {StartMoving}
OnWindow Mod1 Mouse3 :MacroCmd {Raise} {Focus} {StartResizing BottomRight}

OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu

Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod4 F1 :Workspace 1
Mod4 F2 :Workspace 2
Mod4 F3 :Workspace 3
Mod4 F4 :Close
Mod4 t :toggledecor
```
Just looking at it it seems rather self-explanatory. You may be wondering about the "Mod" keys, though. Mod1 is the ALT button on your keyboard. Mod4 is the 'logo' button - usually one belonging to Microsoft or Apple.

As a point of interest, notice the last line in my config. By using Mod4 t :toggledecor I am able to turn off window decorations by toggling the Windows key+t. (This removes all traces of the Fluxbox window manager from the window; title bar, handle, borders, etc.) There are countless other little tweaks you can make should you want to. Various information on keys can be found scattered about the Fluxbox wiki.


**Styles and Themes**

A common place to store one's styles is in ~/.fluxbox/styles, though you are by no means limited to that directory. (Just make sure you adjust your configurations accordingly.) 

There are two types of styles/themes: those that use 'pixmaps' and those that do not. Normally Fluxbox styles are just a raw configuration file, as you may have seen me post in the past. Pixmap styles, however, push the boundaries on the limitations set by regular styles as they can use small images instead of raw configuration details. There are some absolutely *wicked* pixmap themes out there... the downside is that they require the presence of each image file in a directory where the theme file is located. Normal Fluxbox styles can just be a config file sitting in ~/.fluxbox/styles where as a pixmap style will need to be in ~/.fluxbox/styles/style_name. That directory contains the config file and pixmaps for the specified theme.


**Closing**

Anyway, that's all I have for now. If you have any questions about what I've written, or about actual theming (which I did not cover in this guide), please let me know.

---

### Post by Rodney9 on 2010-03-20
Thank You Narada, a wonderful guide I just found.

I love Fluxbox !

Rodney

---

### Post by Scott82 on 2010-04-02
Hi, very nice guide :D i have a question though.
I'm running Ubuntu 10.04 with fluxbox added in (thus this guide has helped a lot with setting up my menu, etc..... dont like the default that was given at all), and i'm trying to get a icon for sound on the (notification area?). i see you're using volwheel, but i'd rather not use anything that's not in the regular repo for the beta phase at least until 10.04 is released. do you know what i can add to .xinitrc to get the sound icon that's used in gnome going? or will it just not work?

---

### Post by Scott82 on 2010-04-02
nevermind :D got it going

---

### Post by kc8hr on 2012-11-23
Hi Narada,

I have a question about window grouping and the apps file.

I can't seem to get this feature working correctly. Have you had any experience getting applications to start tabbed together. The Fluxbox wiki claims it should work, and gives examples, but they don't work when I try them.

I searched Google, and there seems to be a problem with the apps file in the Fluxbox version from the Ubuntu repos.

Any help would be appreciated!

Thanks,
Tim

---

### Post by oldos2er on 2012-11-23
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

