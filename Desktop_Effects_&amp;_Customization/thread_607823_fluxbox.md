---
title: "fluxbox"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by amik on 2007-11-09
ok i am trying to instal fluxbox and get it working ! BUT...... it doesnt.I installed it from system manager. and when i type fluxbox into the terminal it says:

Warning: Failed to open file(/usr/share/fluxbox/nls/en_US.UTF-8/fluxbox.cat)
for translation, using default messages.
Failed to read: session.tabs
Setting default value
Failed to read: session.ignoreBorder
Setting default value
Failed to read: session.forcePseudoTransparency
Setting default value
Failed to read: session.numLayers
Setting default value
Failed to read: session.tabPadding
Setting default value
Failed to read: session.focusTabMinWidth
Setting default value
Failed to read: session.styleOverlay
Setting default value
Failed to read: session.slitlistFile
Setting default value
Failed to read: session.groupFile
Setting default value
Failed to read: session.appsFile
Setting default value
Failed to read: session.tabsAttachArea
Setting default value
Failed to read: session.modKey
Setting default value
apps file failure
Failed to read: session.screen0.imageDither
Setting default value
Failed to read: session.screen0.opaqueMove
Setting default value
Failed to read: session.screen0.workspacewarping
Setting default value
Failed to read: session.screen0.desktopwheeling
Setting default value
Failed to read: session.screen0.reversewheeling
Setting default value
Failed to read: session.screen0.autoRaise
Setting default value
Failed to read: session.screen0.clickRaises
Setting default value
Failed to read: session.screen0.decorateTransient
Setting default value
Failed to read: session.screen0.rootCommand
Setting default value
Failed to read: session.screen0.resizeMode
Setting default value
Failed to read: session.screen0.windowMenu
Setting default value
Failed to read: session.screen0.followModel
Setting default value
Failed to read: session.screen0.window.focus.alpha
Setting default value
Failed to read: session.screen0.window.unfocus.alpha
Setting default value
Failed to read: session.screen0.menu.alpha
Setting default value
Failed to read: session.screen0.menuDelay
Setting default value
Failed to read: session.screen0.menuDelayClose
Setting default value
Failed to read: session.screen0.menuMode
Setting default value
Failed to read: session.screen0.overlay.lineWidth
Setting default value
Failed to read: session.screen0.overlay.lineStyle
Setting default value
Failed to read: session.screen0.overlay.joinStyle
Setting default value
Failed to read: session.screen0.overlay.capStyle
Setting default value
Failed to read: session.screen0.windowScrollAction
Setting default value
Failed to read: session.screen0.windowScrollReverse
Setting default value
Failed to read: session.screen0.tabs.intitlebar
Setting default value
Failed to read: session.screen0.tabFocusModel
Setting default value
BScreen::BScreen: an error occured while querying the X server.
        another window manager already running on display :0.0
Error: Couldn't find screens to manage.
Make sure you don't have another window manager running.


how do i disable the other window manager....please anyone!!! how can i get it wokring

---

### Post by spupy on 2007-11-09
When you are at the login screen (where you enter username/pass before entering GNOME/KDE), there should be a menu called "Sessions" (it can be a button, too). From this menu you can select Fluxbox or other Window Manager/Desktop Environment. 
But that solves only this message: 
```
BScreen::BScreen: an error occured while querying the X server.
another window manager already running on display :0.0
```
The previouse messages look like another problem, with the configuration file of fluxbox.

---

### Post by cknight on 2007-11-10
Do you have a ~/.fluxbox/init file?  If so, post the contents.

---

### Post by RedSquirrel on 2007-11-10
After you install the fluxbox package, run the following command to create the default menu:

```
sudo update-menus
```

Then, logout of your current session. As mentioned above, select "Fluxbox" from the Sessions list and login. Fluxbox will load and everything will be fine.

And don't worry about the other error messages. Everything will be sorted out once you login to Fluxbox as described. ;)


PS - If you want a more complete menu, see the link in my signature.

---

### Post by spupy on 2007-11-10
> **RedSquirrel said:**
> PS - If you want a more complete menu, see the link in my signature.

Whoa, thank you! Your howto is epic.

---

### Post by missmoondog on 2007-11-10
exactly what i was just looking for. simple little command, sudo update-menus, worked like a charm.

didn't have to do that on another machine i just installed fluxbox on though. didn't get all the menu items showing up on that machine as there are now on this one, so will have to remember this on other machines i'm going to put fluxbox on.

thanks

---

