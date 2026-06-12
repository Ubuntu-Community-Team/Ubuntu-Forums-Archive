---
title: "Disable window maximize when titlebar dragged to top of screen?"
date: 2011-04-29
forum: Desktop Environments
---

### Post by wch on 2011-04-29
I just updated to 11.04. I tried to keep an open mind while using Unity, but I just couldn't deal with the totally unorganized application menu, so I switched back to the regular Gnome desktop.

There's something that bugs me, though: when I drag the titlebar of a window up to the top of the screen, it maximizes the window, or more accurately, it "grows" the window depending on how far up I drag it, up to the maximum size of the screen. I don't have any desire to use this method to make my windows larger, and it also prevents me from dragging windows to the virtual desktop above the current one (I have edge-flipping turned on).

Does anyone know how to disable this? I installed the compiz config manager installed but can't seem to find the right option.

---

### Post by Copper Bezel on 2011-04-29
The plugin you need to disable is called the "Grid." = )

---

### Post by wch on 2011-04-29
> **Copper Bezel said:**
> The plugin you need to disable is called the "Grid." = )

Worked like a charm. Thank you!

---

### Post by Copper Bezel on 2011-04-29
Cool. = ) Just please mark the thread as "Solved." (Thread Tools, upper right.)

---

### Post by JafoFubar on 2011-05-01
> **Copper Bezel said:**
> The plugin you need to disable is called the "Grid." = )

Thanks. This helped me too. I find every time I go to a new version of Ubuntu hoping to enjoy new features, I end up spending all my time figuring out how to get rid of the new "features".

---

### Post by stevecomrie on 2011-05-01
Personally I think The Grid plugin has some neat features in it like letting you resize windows using Ctrl+Alt+Number Pad.

If you want to keep that functionality but remove the Maximize when you drag a window to the top do the following:

- Open CompizConfig Settings Manager
- Click on the "Grid" in the "Window Management" category
- Click on the "Edges" tab
- Open the "Resize Actions" drop down
- Change the "Top Edge" drop down to "None"
- Close CompizConfig and you're all done.

---

### Post by Marji on 2011-06-13
Note that if you don't have the CompizConfig Setting Manager installed, you can use gconf-editor (start it from terminal) and go to :

- apps -> compiz-1 -> pluging -> grid -> screen0 -> options -> top_edge_action

set this value to 0

relief! :)

---

### Post by malspa on 2011-07-06
> **stevecomrie said:**
> If you want to keep that functionality but remove the Maximize when you drag a window to the top do the following:

- Open CompizConfig Settings Manager
- Click on the "Grid" in the "Window Management" category
- Click on the "Edges" tab
- Open the "Resize Actions" drop down
- Change the "Top Edge" drop down to "None"
- Close CompizConfig and you're all done.

> **Marji said:**
> Note that if you don't have the CompizConfig Setting Manager installed, you can use gconf-editor (start it from terminal) and go to :

- apps -> compiz-1 -> plugins -> grid -> screen0 -> options -> top_edge_action

set this value to 0

Very nice tips -- thanks!

---

### Post by jrbray on 2011-10-25
Good, that's been annoying me for months. I wish Ubuntu wouldn't introduce new functionality that upsets the status quo without warning, but that seems their policy now, and why I'm moving to Mint.

---

### Post by fiazseo on 2011-10-25
Great. = ) Just please level the place as "Solved." (Thread Methods, second right.)

---

### Post by jerrysiii on 2011-10-26
Just moved to Mint a few days ago.  Since it's based on Ubuntu, it also had this "feature".  I found this thread very helpful in disabling.  Thanks stevecomrie!

Too bad though, I've been with Ubuntu since 8.04.  Unity is a big step backwards.  It may be ok for novice uses that like to run apps full screen.  Otherwise the global menu is awful.

---

### Post by jimav on 2012-08-10
If disabling compiz grid doesn't help (or it wasn't enabled to begin with), visie "Workspace Behavior" in the regular KDE System Settings.  It has a "Screen Edges" tab in which "Maximize windows by dragging them to the top of the screen" is an option.

For me, un-checking that solved the problem.

---

