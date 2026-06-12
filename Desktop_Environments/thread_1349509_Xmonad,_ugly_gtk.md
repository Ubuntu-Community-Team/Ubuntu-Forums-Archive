---
title: "Xmonad, ugly gtk"
date: 2009-12-08
forum: Desktop Environments
---

### Post by graabein on 2009-12-08
Hi, I've been wanting to try a tiling window manager for quite some time. Yesterday I finally installed [xmonad]("http://tombuntu.com/index.php/2009/03/17/introduction-to-the-xmonad-tiling-window-manager/") and I like it quite well, except the controls and fonts are ugly as hell compared to my GNOME setup. Can I do anything about this? How?

Another problem I'm having is some kind of lag in Firefox. Sometimes the mouse events aren't picked up but it responds to keyboard shortcuts. It usually disappears after some seconds or by switching to and from another virtual desktop. 

Other than that I have a really good impression! :D

---

### Post by akashiraffee on 2009-12-08
> **graabein said:**
> Hi, I've been wanting to try a tiling window manager for quite some time. Yesterday I finally installed [xmonad]("http://tombuntu.com/index.php/2009/03/17/introduction-to-the-xmonad-tiling-window-manager/") and I like it quite well, except the controls and fonts are ugly as hell compared to my GNOME setup. Can I do anything about this?

Probably not.  I think GNOME uses it's own font server, which has a bit more polish than the Xorg one -- which is what Xmonad probably uses.  I assume Xmonad is designed to run on a wide range of *nix type systems in a standardized way, which GNOME is not constrained by such considerations.

The window controls, such as the titlebar, etc, are produced by the window manager.  The widgets themselves (buttons inside the window, etc.) should appear the same IF the gtk theme is still the same.  If not you may need to use a .gtkrc file in ~ to set the theme, I have not done that in long time, but I believe it still works.

---

### Post by m_duck on 2009-12-08
To answer your first question, there are a couple of choices. The first one (what I do) is use an app like lxappearance. This will allow you to set your GTK theme as well as fonts and icons. This is basically the same as akashiraffee's suggestion as lxappearance will just create the ~/.gtkrc-2.0 file for you. The second option I can think of is running [XMonad inside GNOME](http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Gnome). That will given you normal GNOME functionality but with XMonad replacing metacity as the window manager.

---

### Post by graabein on 2009-12-08
Thanks guys. I'm gonna try lxappearance. I've used LXDE on an older computer before. Pretty good stuff.

---

### Post by graabein on 2009-12-14
Well [lxappearance]("http://sourceforge.net/projects/lxde/files/LXAppearance/") did the trick for the look, but the feel is not too good... Sometimes mouse clicks don't get passed to the active window. I have to switch back and forth between desktops to get it working again. Keyboard events are passed to active window with no problems though. 

Any ideas? :(

---

