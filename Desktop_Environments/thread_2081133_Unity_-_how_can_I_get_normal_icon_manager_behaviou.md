---
title: "Unity - how can I get normal icon manager behaviour?"
date: 2012-11-06
forum: Desktop Environments
---

### Post by ArlieS on 2012-11-06
Unity has imported a feature from mac OS/X which I find inconvenient. An friend told me it was possible, somehow, to disable this feature, but a web search isn't helping, perhaps because I don't know what the feature is called.

Here's the problem. Suppose I have multiple windows of the same type open. Perhaps they are all firefox windows; perhaps they are all terminal windows.  I want to find a specific one and use it, i.e. raise it to the top of my heap of windows and select it. 

On most window managers, there's some way to get a list of all the windows associated with a particular program, or process - or to simply get a list of windows sorted in some way, and click on one of them.  A few don't provide lists - they merely provide icons, or thumbnails, which are often much harder to identify than text-based titles. A few particularly unpleasant ones use hard-to-identify images _and_ keep moving the images around, so you can't even remember your windows by icon/thumbnail location.

Unity, unfortunately, is in this last category - I click on e.g. the firefox icon in the bar on the left side of my unity desktop, and it selects one of the windows of that type. If I click while a window of that type is selected it displays a screen with nothing but windows of that type, tiled across the screen, and *reduced in size so they'll all fit*. If I can identify the right window from its shrunken image, I can then select it. But if I have several with a similar pattern, and need to read text to identify the desired window, I'm stuck picking randomly, and hoping I get the right one. And most painful of all, when I get the wrong one, and go back to the selection screen, the windows are tiled in a new order, so I can't simply try the next likely looking one.

What I want is a way to tell Unity that what I want in this situation is a list of window titles - the string one might set with "-T I_am_a_title" when launching the window, and which well behaved X applications often set based on window contents.  That would give me parity with such advanced window managers as twm, which dates back to 1988.

In case this matters, I'm running Ubuntu desktop 12.04.

---

### Post by jerome1232 on 2012-11-06
Have you tried poking around in ccsm looking for options related to the window switcher? if not try it, install ccsm but be careful with enabling/disabling plugins. some don't get along with the unity plugin so well.

---

### Post by ArlieS on 2012-11-06
> **jerome1232 said:**
> Have you tried poking around in ccsm looking for options related to the window switcher? if not try it, install ccsm but be careful with enabling/disabling plugins. some don't get along with the unity plugin so well.

I just googled ccsm, and get the impression that the folks developing Unity don't like it and intend to break it. This is phrased as "ccsm has no future; the future plans for Unity are to migrate all the  useful configurability bits out of ccsm into safer, supported tools.  These tools should start to appear in 12.04." (See [http://askubuntu.com/questions/80589/what-are-some-of-the-issues-with-ccsm-and-why-would-i-want-to-avoid-it](http://askubuntu.com/questions/80589/what-are-some-of-the-issues-with-ccsm-and-why-would-i-want-to-avoid-it)) 

I'm somewhat afraid to use it - mostly because I fear there's no way to save an existing configuration and fall back to it if something gets broken. Also, it's easy to imagine the very next update to my Ubuntu system failing messily because of something I'd done with ccsm - which worked perfectly well with a slightly earlier version of Unity. 

I'd be overjoyed to have a window manager that "just worked", possibly requiring configuration with its own built-in tools, but I'm not sure that Unity even wants to go that route, except for a very limited set of options. 

Failing that, I could live happily with a Unix-style window manager, controlled by text based configuration files, documented by complete and accurate man pages and/or explanatory comments in the default versions of those files. 

I'm beginning to fear that no modern window manager supports that strategy either. 

Is it time to uninstal unity and replace it with tvtwm?

---

### Post by ArlieS on 2012-11-06
Aha - If I do Alt ` - I get the same silly thumbnails, but I can step through them by repeating Alt `, and a text name for the current one is displayed at the bottom of the screen.  I can pick my window by releasing the alt key when the desired window is selected. 

That seems to be one variant of the "switcher" - not to be confused with whatever I get when I click twice on an icon in the left bar :-( 

It's not as good as getting a list and clicking on one by name, but at least it's usable. 

Thank you very much for giving me the keyword "switcher" - googling "unity switcher" gave me the recipe,  expressed in terms of alt-<key above tab>. 

Sometimes I'm convinced there's a decent window manager lurking inside Unity, that will emerge if/when the development team documents their baby instead of relying on it to be "intuitively obvious" to users. That's why I haven't uninstalled it, in spite of repeated frustration. 

But then there are the other times, when I'm convinced that window managers went down the wrong path in Windows, and unfortunately everyone else followed, so nothing is ever going to improve on tvtwm.

---

### Post by stinkeye on 2012-11-06
There is the window-list indicator.
**_[COLOR="DarkRed"]https://launchpad.net/~jwigley/+archive/window-list[/COLOR]_**
[ATTACH]226766[/ATTACH]


Also when using the default window spread it uses the scale plug in compiz.
If you enable the **Scale Addons** plugin in ccsm, you can
 zoom a window in the spread with right mouse and close with middle click.
[ATTACH]226767[/ATTACH]  [ATTACH]226768[/ATTACH]

---

### Post by jerome1232 on 2012-11-06
> **ArlieS said:**
> I just googled ccsm, and get the impression that the folks developing Unity don't like it and intend to break it. This is phrased as "ccsm has no future; the future plans for Unity are to migrate all the  useful configurability bits out of ccsm into safer, supported tools.  These tools should start to appear in 12.04." (See [http://askubuntu.com/questions/80589/what-are-some-of-the-issues-with-ccsm-and-why-would-i-want-to-avoid-it](http://askubuntu.com/questions/80589/what-are-some-of-the-issues-with-ccsm-and-why-would-i-want-to-avoid-it)) 


For now, we don't have all of those tools, so we have to use ccsm for some things.

All you have to do to reset unity and compiz is run this little command
```
unity --reset
``` Also firefox has this group tabs feature, where you can have a grip of tabs open you click the button and it will go into a mode similiar to Unity's window spread, but it has the title text like you want. See attached screenshot.

---

### Post by black veils on 2012-11-07
if you dont have any particular use for unity, then you could install another desktop onto your current system, like xfce - nearly everything is configurable.

```
sudo apt-get install xfce4
```
or
```
sudo apt-get install xubuntu-desktop
```
or
```
sudo apt-get install gnome-session-fallback
```

---

