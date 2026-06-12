---
title: "Gnome 3.2- Help!"
date: 2011-10-21
forum: Desktop Environments
---

### Post by cortman on 2011-10-21
What happened to Gnome in 3.2?

I am fervently hoping I'm just dumb and haven't figured out how to edit stuff yet, but I find I am unable to

a) decide whether background should be center, zoom, tile, etc.
b) use a screensaver, and which one
c) add or remove toolbars
d) add or remove widgets on toolbars
e) edit desktop themes (things like window bars, etc. that I could do easily in Natty Gnome)
f) change icon theme
g) minimize open windows (all I have is an “x” at the upper right corner??)
h) change size of icons on favorites bar, and also in the application selection window?

These are just a few that come to mind
I want to like Gnome 3.2. There are some things I definitely like about it already, but surely there are some more customization settings out there??
I would really appreciate some knowledgeable help.
Thanks!

---

### Post by crdlb on 2011-10-21
a) You can do that when you add a custom image. That setting just doesn't show up for the default wallpapers

b) You might be able to use xscreensaver. I expect we'll see some clutter-based screensavers once the screen locker is integrated into the Shell (not that I plan on using one).

c,d) These are possible to various degrees with Shell extensions, for instance: [http://intgat.tigress.co.uk/rmy/extensions/index.html](http://intgat.tigress.co.uk/rmy/extensions/index.html)

e,f,g) You can install [gnome-tweak-tool]("apt:gnome-tweak-tool")

h) There's probably an extension to make the application selector icons smaller, but the ones in the dash shrink automatically as needed.

---

### Post by cortman on 2011-10-22
OK, with a little research I've managed to figure out a good bit of this out. It's not as bad as I thought.
My biggest thing I'd like now would be customizable toolbars. I liked having the "force quit" and other buttons handy on the main bar. Any way I can get that back?

---

### Post by Alwimo on 2011-10-22
It's not the top panel, but there is a Force Quit launcher (dock) app.
[http://www.omgubuntu.co.uk/2011/10/freezeunfreeze-unity-app-killer/](http://www.omgubuntu.co.uk/2011/10/freezeunfreeze-unity-app-killer/)

I thought I saw someone made a panel one for 11.10 but I might have imagined it.

---

### Post by crdlb on 2011-10-22
I would just set up a keyboard shortcut that runs xkill.

I found a [force quit extension]("http://motorscript.com/gnome-shell-extension-force-quit/"), but it needs to be updated for 3.2

---

### Post by OzzyFrank on 2011-10-22
> **cortman said:**
> OK, with a little research I've managed to figure out a good bit of this out. It's not as bad as I thought.
My biggest thing I'd like now would be customizable toolbars. I liked having the "force quit" and other buttons handy on the main bar. Any way I can get that back?

Yes, **force quit** was one of the main things I was missing on upgrading to 11.10. No need to test out third-party apps and extensions - simply **[COLOR="Red"]hold Alt while you right-click an empty area of your panel[/COLOR]**, choose **[COLOR="Purple"]Add to Panel...[/COLOR]**, and add it just like you did the first time! Basically all the same launchers and widgets are there, except notably **drawers**, which were deliberately removed as they wouldn't work well in Gnome 3 without a rewrite.

(PS: This is in the GNOME Classic desktop, in case that makes a difference).

---

### Post by crdlb on 2011-10-22
> **OzzyFrank said:**
> 
(PS: This is in the GNOME Classic desktop, in case that makes a difference).

It does, in fact. GNOME Shell does not have applets.

---

### Post by OzzyFrank on 2011-10-22
Oh, and (at least in the Classic desktop) you can drag launchers from your menu to the panel (you would have noticed you can't right-click and choose to add them to the panel any more), and for location shortcuts, just drag the folder in question to the panel (in this regard, it's better than Gnome 2.x). To remove or move launchers, once again the trick is to **[COLOR="Red"]hold Alt while right-clicking[/COLOR]**.

---

### Post by OzzyFrank on 2011-10-22
> **crdlb said:**
> It does, in fact. GNOME Shell does not have applets.

Oh well. I thought it was worth a shot since both are Gnome 3. Figured there might be an issue in Shell, since the top panel is now used like in Unity/Mac. For those of us using Classic, at least we can get our panels back to almost as they were (really missing drawers!).

---

### Post by cortman on 2011-10-24
OK, after playing with it over the weekend, 3.2 isn't as bad as I thought. I'm getting used to several new features of it and some things are nice, like the open-window selector.
Just one thingw would make it really nice: give back the ability to create extra panels, and add widgets to said panels. I looked up a couple recommendations for scripts to solve this but they all seem to be for Gnome 3.

---

