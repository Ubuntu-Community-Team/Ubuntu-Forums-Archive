---
title: "Windows 7 Explorer Functionality Possible?"
date: 2010-01-05
forum: Desktop Environments
---

### Post by Tu1J4kXk8NUhMz on 2010-01-05
This is a curiosity, so if there's no answer so be it. In Windows 7, you can do a number of things to compare Explorer windows: you can stand them side-by-side, stack them, and (the coolest feature IMO) you can stretch the window to the full height of the screen by pulling the top border off the screen.

I suspect I'm not describing this very well, but if you've used Win7 I hope you know what I'm talking about. Is there some way to implement this same functionality in Ubuntu?

---

### Post by Twitch6000 on 2010-01-05
> **teamjh14 said:**
> This is a curiosity, so if there's no answer so be it. In Windows 7, you can do a number of things to compare Explorer windows: you can stand them side-by-side, stack them, and (the coolest feature IMO) you can stretch the window to the full height of the screen by pulling the top border off the screen.

I suspect I'm not describing this very well, but if you've used Win7 I hope you know what I'm talking about. Is there some way to implement this same functionality in Ubuntu?

This is indeed possible (well besides that side by side thing) all you need is compiz then pick in the settings what you want.

---

### Post by mocoloco on 2010-01-05
FYI, the term you want to use is "window manager", not explorer.  The windows manager is what's responsible for how they're resized, maximized, etc.
Adding to what Twitch6000 suggested, it's at least partially possible with compiz.  Make sure you have installed "Advanced Desktop Effects Settings" (search for compiz config in the software center).  Under window management > maximize there are options to maximize up and down only, etc.

I'm sure it's possible to mimic more of the windows 7 window management features, google and I'd bet someone's done it or is working on it.

---

### Post by Tu1J4kXk8NUhMz on 2010-01-05
> **mocoloco said:**
> FYI, the term you want to use is "window manager", not explorer.  The windows manager is what's responsible for how they're resized, maximized, etc.
Adding to what Twitch6000 suggested, it's at least partially possible with compiz.  Make sure you have installed "Advanced Desktop Effects Settings" (search for compiz config in the software center).  Under window management > maximize there are options to maximize up and down only, etc.

I'm sure it's possible to mimic more of the windows 7 window management features, google and I'd bet someone's done it or is working on it.

While your terminology is definitely more descriptive (and what I was actually trying to come up with), the Windows File Manager is called Windows Explorer. I knew it was labeled this at one point, but I guess it still is, even in Windows 7. (SOURCE: [http://en.wikipedia.org/wiki/Windows_Explorer](http://en.wikipedia.org/wiki/Windows_Explorer) )

I'll take a look around. I didn't think Compiz had that kind of functionality...must not have played with it enough. Thanks for the info, guys, I'll have to mess with Compiz some more!

---

### Post by Prendi on 2010-01-05
> **teamjh14 said:**
> While your terminology is definitely more descriptive (and what I was actually trying to come up with), the Windows File Manager is called Windows Explorer. I knew it was labeled this at one point, but I guess it still is, even in Windows 7. (SOURCE: [http://en.wikipedia.org/wiki/Windows_Explorer](http://en.wikipedia.org/wiki/Windows_Explorer) )

Yes, it's still called "Explorer" in Windows 7, but that's besides the point. What the OP meant was that being able to stack Explorer windows or maximize them vertically is not a functionality of the Explorer, but of a window manager (called "Desktop Window Manager" in Windows Vista and 7) that provides this functionality to all other windows as well, not just Explorer windows. 
Thus, the functionality you described has nothing to do with the Explorer, and the thread title you chose might be confusing.

no offense...

---

### Post by HTML-insane on 2010-01-05
Interestingly, this stuff is in KWin for KDE 4.4 release. I don't touch it myself - it's a most irritating behaviour at best, and if I'm doing file-management stuff (like copying/moving files etc.), I can just do it in one Dolphin window and split the view. Job's a good'n!

---

### Post by Tu1J4kXk8NUhMz on 2010-01-06
> **Prendi said:**
> Yes, it's still called "Explorer" in Windows 7, but that's besides the point. What the OP meant was that being able to stack Explorer windows or maximize them vertically is not a functionality of the Explorer, but of a window manager (called "Desktop Window Manager" in Windows Vista and 7) that provides this functionality to all other windows as well, not just Explorer windows. 
Thus, the functionality you described has nothing to do with the Explorer, and the thread title you chose might be confusing.

no offense...

Ah, I see what you mean. Touche. Thanks for the point of clarification.

As an update, I've poked around a bit in Compiz and haven't found anything. Still working on it though. I'd be interested to see what KDE has to offer, HTML, as I have very little experience with it.

---

### Post by airtonix on 2010-01-07
> **teamjh14 said:**
> Ah, I see what you mean. Touche. Thanks for the point of clarification.

As an update, I've poked around a bit in Compiz and haven't found anything. Still working on it though. I'd be interested to see what KDE has to offer, HTML, as I have very little experience with it.

sorry. Windows Explorer doesn't have as much functionality as any linux window manager.

1. can't middle click maximise button to vertically maximise.
2. can't right click maximise button to horizontally maximise.
3. can't hold alt and right click drag to easily resize windows.
4. can't hold alt and left click drag to easily move windows.

Metacity, Kwin, Openbox, Blackbox, XFCE, Compiz all provide these very handy shortcuts.

To get them in windows you need to install extra software. 

points 3 & 4 can be addressed by using winxmove ([http://sourceforge.net/projects/winxmove/](http://sourceforge.net/projects/winxmove/)) or taekwindow ([http://taekwindow.sourceforge.net/](http://taekwindow.sourceforge.net/)).

i haven't found a way to provide points 1 & 2 on windows without causing either : 
 a) bloat (windows blinds)
 b) total conversion (bb4win)

---

### Post by hariks0 on 2010-01-07
I do not remember what I have set to maximise window with vertical mouse drag on title bar. But you can try importing my attached ccsm profile file. It also contains some windoze like keyboard bindings as described in the link at my signature.

BTW, the only thing I want from windoze explorer is the ability to filter the files in accordance with the items in the drop down list beside the fields in explorer. For example, by clicking the Type field drop down menu, one can select only a specific type of files to be listed and by clicking the size filed drop down menu, one can select only files size of which is between a range/less than/greater than a value to be listed in the window.

---

### Post by hariks0 on 2010-01-07
Sorry! I cannot upload the file. It is not getting attached.

---

