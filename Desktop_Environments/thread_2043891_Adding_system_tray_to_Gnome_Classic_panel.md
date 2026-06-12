---
title: "Adding system tray to Gnome Classic panel"
date: 2012-08-17
forum: Desktop Environments
---

### Post by Only1KW on 2012-08-17
I recently switched to Gnome Classic on my 11.10 installation and am trying to get it configured.  As I have multiple monitors, I'd like to have a panel for each screen/monitor.

By default, the panel at the top of the primary monitor on the right side had what I would call a system tray.  It contains my battery monitor and volume control, among other things.  I am trying to add that same thing to the panel on my secondary monitor, but so far have had no luck.  None of the "items" that I can add to my panel seem to indicate anything about being a system tray.  From my research, it sometimes seems to indicate that the "Notification Area" is the same thing, but if I add that to any panel, it seems to be empty and I can find no way to add any icons to it.  My research has also found references to a gnome-shell-classic-systray package that I need, but when I try to install it, apt can't locate that package.  Any other thoughts?

---

### Post by Only1KW on 2012-08-20
Bump.

This should be basic functionality.  No one knows how to do this?

---

### Post by DoubleClicker on 2012-08-20
There is no such thing as a "system tray"  on a linux system.  What you want is  ubuntu's  "indicator applet" or "indicator applet complete".

I don't believe that indicator applets were ever added to the 11.10 repositories (I could be wrong), so they need to be added with a ppa

sudo add-apt-repository ppa:jconti/gnome3
sudo apt-get update
sudo apt-get install indicator-applet indicator-applet-complete indicator-applet-session indicator-applet-appmenu

---

### Post by kansasnoob on 2012-08-21
> **DoubleClicker said:**
> There is no such thing as a "system tray"  on a linux system.  What you want is  ubuntu's  "indicator applet" or "indicator applet complete".

I don't believe that indicator applets were ever added to the 11.10 repositories (I could be wrong), so they need to be added with a ppa

sudo add-apt-repository ppa:jconti/gnome3
sudo apt-get update
sudo apt-get install indicator-applet indicator-applet-complete indicator-applet-session indicator-applet-appmenu

+1!

Step #2 here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

---

### Post by Only1KW on 2012-08-21
I did notice that option.  Just not really thrilled about adding third-party repositories and the risks involved with that, especially when it's obvious that one instance of the item I'm interested in (which apparently is only called the systray in Unity) already exists by default in Gnome, and all I want to do is add another one.

I did some more searching and found [this]("http://askubuntu.com/questions/78240/where-does-gnome-3-store-panel-orientation") which describes how to use dconf-editor to see details about the Gnome panel.  From that, I can very clearly see that the item that already existed by default that I am interested in is a "NotificationArea" object.  But still, adding new Notification Area items to any panel does not show any of the icons in the default Notification Area (battery, sound, network).  At this point, I'm throwing in the towel and writing this off simply as a bug.

---

### Post by vexorian on 2012-08-21
hmnn, in my setup (12.04, fallback gnome panel) the applet thing that holds all the indicators is called "miniaplicación completa de indicadores). I guess in English it is something like "complete indicator mini-applet". 

There is another applet called "Notification area", but when I tried it, it added nothing. 

I tried adding multiple panels of the "mini-applet" and it works fine. Its icon is a single blue circle with the "information" i inside. Whereas the applet that does not work also has a panel in the icon.

---

### Post by Only1KW on 2012-08-22
It's called "Indicator Applet Complete" in English in 12.04.  Works great in my experience too.  But the same package doesn't exist in the default stable repository for 11.10.

---

### Post by BadBrains on 2013-05-17
_Mistake sry guys, my post was for a different theme._

---

