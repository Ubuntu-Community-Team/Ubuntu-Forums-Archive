---
title: "small KDE inteface problems"
date: 2005-10-03
forum: Desktop Environments
---

### Post by cypher35 on 2005-10-03
I'm still somewhat new to KDE, and i have a few small problems with the interface.  I know some of these may seem like small nitpicks, but they really hinder my productivity due to lack of familiarity.  Please let me know if there these have workarounds or if what i'm saying makes no sense.
Here are my problems in no particular order:
[LIST]
[*]When an item on the desktop is highlighted, i'm used to the name being shown in it's entirety instead of ending in "...".  I realize that you can hit F2 to see it, or idle the cursor over it for a few seconds to get a detailed popup, but it's not the same.  I doubt it would be that hard of a feature to implement.  Also, how about clicking on a higlighted item to rename it?
Furthermore, when the icon size or font size are adjusted for the desktop, the cutoff "..." remains in the same place regardless of the extra space given by the size reduction:
[IMG]http://i2.photobucket.com/albums/y7/cypher35/desktop_example.jpg[/IMG]
[*]Resizing a window seems needlessly complicated...  I have to line up the cursor on a 1px frame to get the dual-arrow resize cursor to show up.  Is there any way to get kde to allow resizing within +-3px from the border without increasing the physical look of the border size to the "Very Huge" setting?  I also realize that there are keyboard shortcuts to resize the window but i prefer the former.
[*]Is there a way to get Konqueror to default to the "Detailed List View" when it opens up instead of "Icon View"?
[*]In Firefox when you launch the icon after firefox is already open, it will open a new window instead of starting a new instance of firefox.  However, in KDE when this occures and a new firefox window is open, a placeholder in the taskbar acts like firefox is being started up (spinning hour glass icon and the like) and the bouncing firefox icon appears next to the cursor.  Apparently kde doesn't realize that it has already accomplished it's task and pretends to launch a new instance of firefox until it times out (20 seconds or so).  Is there any fix for this?
[*]there may be more, but this is all i can remember for the time being...
[/LIST]
Any feedback would be greatly appreciated...

---

### Post by GameManK on 2005-10-03
[QUOTE=cypher35]In Firefox when you launch the icon after firefox is already open, it will open a new window instead of starting a new instance of firefox.  However, in KDE when this occures and a new firefox window is open, a placeholder in the taskbar acts like firefox is being started up (spinning hour glass icon and the like) and the bouncing firefox icon appears next to the cursor.  Apparently kde doesn't realize that it has already accomplished it's task and pretends to launch a new instance of firefox until it times out (20 seconds or so).  Is there any fix for this?[/QUOTE]

just want to say I also find this to be an annoying issue with Firefox and Opera, and a fix would be nice. Though it usually only comes up when somebody unfamiliar with linux tries to use my computer and double-clicks the icon.

As to resizing windows, KDE seems the same to me as any other OS so I'm not sure what the problem is.. but maybe somebody has a nice trick for you

I haven't tried it, but I would think if you set your icon behavior to double clicking to open then you would be able to click a highlighted item to rename it.

---

### Post by mlomker on 2005-10-03
> I doubt it would be that hard of a feature to implement.  Also, how about clicking on a higlighted item to rename it?

These are KDE design decisions and not a Ubuntu feature.  They are making radical changes in v4.0, so we'll see what happens there.

> Is there a way to get Konqueror to default to the "Detailed List View" when it opens up instead of "Icon View"?

A fine question, since that is also my preference.  I'll look into that further in the morning.

> However, in KDE when this occures and a new firefox window is open, a placeholder in the taskbar acts like firefox is being started up (spinning hour glass icon and the like) and the bouncing firefox icon appears next to the cursor. 

Mine only does that until I hit the 'stop' button.  It doesn't consider Firefox loaded until it brings up the homepage that I have specified.  Does your icon point to **firefox %u** or  another executable?  I change mine from the default.

Mouse settings are in the Control Center under Peripherals, Mouse.  Also look under Appearance & Themes, Launch Feedback.  I set the *startup indication timeout* to 4 seconds, which is easier to live with.

---

### Post by GoldBuggie on 2005-10-04
>  Is there a way to get Konqueror to default to the "Detailed List View" when it opens up instead of "Icon View"?

For ordinary home browsing I think you only need to change it to "Detailed List View" and then "Save View Profile".

But this never solved the trouble of Icon View always showing when I used the "storage media". But I finally found a solution to the problem.

You can right-click on a folder. Go to properties. Then click on the icon at the right of the text "Type: Folder". From there go to the Embedding Tab and you will see a list of all the different views and in with order they are chosen. Move the Detailed List View to the top and you will always get that view first.

---

### Post by claydoh on 2005-10-04
> Is there a way to get Konqueror to default to the "Detailed List View" when it opens up instead of "Icon View"?

Yes, you can do this. Just set Konqueror the way you want it to look, then go to "Settings" on the menubar, then click on "Save View Profile Kubuntu File Manager" (it might be called something else). Then Click on "save" in the bottom of the new dialog that pops up.

---

### Post by odrop on 2005-10-04
[QUOTE=cypher35]
Resizing a window seems needlessly complicated...  I have to line up the cursor on a 1px frame to get the dual-arrow resize cursor to show up.  Is there any way to get kde to allow resizing within +-3px from the border without increasing the physical look of the border size to the "Very Huge" setting?  I also realize that there are keyboard shortcuts to resize the window but i prefer the former.
[/QUOTE]

This depends a little on what window decorations you're using and what it allows to be changed.
Goto... KDE->Preference->Appearance & Themes->Window Decorations
The option you're looking for is Border Size. Some have this option, some don't.  Like Glow and Keramik have this.

Hope this helps you out.

---

### Post by cypher35 on 2005-10-04
Thanks for all the feedback, i think that did the trick...

Everything accept for the desktop filenames, but i guess that can't be helped.

---

### Post by cypher35 on 2005-10-04
I found a nice way to get past that firefox problem i've been having, and it didn't involve changing the application launch feedback for the entire system...

Apparently, in the K Menu settings, you can change application-specific launch feedback.  I told it not to give any feedback on firefox and voila! It works like a charm!

---

### Post by mlomker on 2005-10-04
> Apparently, in the K Menu settings, you can change application-specific launch feedback.  I told it not to give any feedback on firefox and voila! It works like a charm!

I hear ya, but I had other things like rdesktop scripts that took forever as well.

---

