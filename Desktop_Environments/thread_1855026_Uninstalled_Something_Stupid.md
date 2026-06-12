---
title: "Uninstalled Something Stupid"
date: 2011-10-05
forum: Desktop Environments
---

### Post by roadkillguy on 2011-10-05
I'm using Ubuntu 11.04 on my netbook.  I was cleaning up a few applications that didn't work, and for whatever reason my Places->X menu didn't work.  It simply said "No application is registered as handling this file".  I meant to ask about this, but I kinda put it off.  After restarting my computer, all hell has broken loose.  My windows have no borders, my taskbar doesn't display current windows, and unfortunately my screenshot hotkey doesn't work.  (I'm not sure what the screenshot program is called, otherwise I would do it in the terminal.)

What package controls this?  Nautilus is still installed.

---

### Post by Copper Bezel on 2011-10-05
The command is gnome-screenshot.

Does running compiz --replace bring back your window borders?

Which application were you using to remove the packages? The Software Center and Synaptic both have "history" features to show which packages you've removed lately, which should help to narrow down the possibilities.

---

### Post by roadkillguy on 2011-10-05
I used Software Center.. I'm looking through those now.

compiz --replace definitely brought back the borders.  Why didn't that run at startup?

I'm still having that Places->FolderX problem.  How do I set an application as handling that?

Maybe I should backup my data and reinstall Ubuntu.

---

### Post by roadkillguy on 2011-10-05
Nothing in the list of packages seems at all related to compiz.

To fix the Places Menu Problem, tutorials online say to right click a folder and use a special command (in this case nautilus) to open it.  Unfortunately, it doesn't change anything.  (I think it's recognizing the file as a folder, and thus not saving what I opened it with.)

---

### Post by Copper Bezel on 2011-10-05
Do you have XFCE or any XFCE utilities installed?

Confirm something for me - run this:

```
xdg-open ~
```

And could I see the contents of the file ~.local/share/applications/mimeapps.list?

> compiz --replace definitely brought back the borders. Why didn't that run at startup?
It does, but something else is breaking Compiz during the startup process. Normally, that's a result of a recent change in Compiz settings. There's no way to identify which one, though. Have you made any recent tweaks in Compiz?

Worst case scenario, we can _[revert Compiz to default settings]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html#ResetCompiz")_ with a couple of quick commands (scroll down to "Reset Compiz".) You shouldn't have to reinstall anything.

Edit: Step two to solving the Places menu problem, by the way, if you *do* have XFCE installed, is to run the command 

```
exo-preferred-applications
```

and check if anything is selected for File Manager under the Utilities tab.

---

### Post by Krytarik on 2011-10-05
> **roadkillguy said:**
> I'm still having that Places->FolderX problem.  How do I set an application as handling that?
Open the file "~/.local/share/applications/mimeapps.list", and make sure "inode/directory" isn't listed under the section "[Removed Associations]", like this:
```
[Removed Associations]
inode/directory=nautilus-folder-handler.desktop;
```This should fix at least fix this issue. ;-)

---

### Post by roadkillguy on 2011-10-05
Sorry guys, already reinstalled 11.04.  I wanted a fresh install anyway, that's why I was removing stuff.

Works great now! :lol:

---

