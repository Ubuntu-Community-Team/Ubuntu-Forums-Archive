---
title: "Thunar behaviour changed"
date: 2016-05-29
forum: Desktop Environments
---

### Post by kazakore on 2016-05-29
Since updating from 14.04 to 16.04, and thus from Thunar 1.6.3 to 1.6.10, there has been a couple of changes in the way that Thunar work that really impinge on my work flow!

1. No longer possible to select multiple files by dragging from over the filename. It still works if dragging is done from white space if in Icon or Compact view, or from a column other than filename in Detailed view, but then not the white space below in Detailed. (I always used Detailed List and have it set to auto-expand the column so sometimes it can end up wider that the window. Plus it really slows me down have to think where to start dragging from! This is the more annoying niggle.)

2. No longer possible to do a RMB drag and drop. There used to be a time within if you started to move the mouse of right clicking you could drag and then get the menu options to Move/Copy/Link/Cancel on release. This is no longer possible.


My searching for possible solutions seemed to imply it could be related to GTK themes but I am running the same theme on both installs under Appearance and have tried multiple under the Windows Manager option (the same as I have on 14.04 isn't listed) and nothing made any difference.

Is there any way to restore these operations?

---

### Post by Dennis N on 2016-05-29
For the first, I just left-click to select the first, then shift-left-click to select the last. Those in between get selected too. That seems quicker than any of the alternatives you describe.

Sorry, no suggestions for the second about the menu, but you can drag and drop to move or copy depending on the use of the shift-key, but you probably already know that.

---

### Post by ajgreeny on 2016-05-29
What file-view do you use?

I am like Dennis N and use a **left click then shift+2nd left click** to select multiple files but I also always use **detailed list view** in my file managers; always have done since my days in Win 3.1, so maybe it is easier for me with that view.

---

### Post by kazakore on 2016-05-31
As mention I always use Detailed List view and this is the worst affected as it doesn't work from the dead space next to the filename on this view.

I know all about the alternative methods of selecting and I do this sometimes (actually I would old Shift and use the Arrow Keys rather than clicking a second time more often), but only really when sat at a desk in a correct posture for typing, whereas if I am using my laptop in my bed on sat on a lounge chair or in anything but the ideal position I find this a lot harder to do quickly and easily then just dragging over the files!

It affects me most severely when organising music for DJ sets. Drag to copy files from Audacity then would usually just drag over two or three files at once to select while changing focus, then Alt+F2 to rename all (by audio tags.) It really makes this a LOT more cumbersome and I don't understand why the functionality would have been removed! Is there no way to change it back. Otherwise I might remove Thunar and reinstall the old version from Trusty and hope that really fixes it and the fault isn't somewhere elsewhere (like some issue with GTK in the new XFCE as was hinted at in my previous searches.)

---

### Post by kazakore on 2016-05-31
Downgraded to the 1.6.3 version from Trusty by taking the thunar and thunar-data packages from that repo and using dpkg. This has restored the old function (and the old bugs such as those related to multi-selection not updating correctly) and makes it much more usable for me.

Have put a feature request to make it configurable on the XFCE forum: [https://forum.xfce.org/viewtopic.php?id=10904](https://forum.xfce.org/viewtopic.php?id=10904)

---

### Post by NadirPoint on 2016-05-31
> **kazakore said:**
> ... No longer possible to select multiple files by dragging...
Actually, it is.  You just need to select/click under the "name" field.

---

### Post by ajgreeny on 2016-05-31
> **NadirPoint said:**
> Actually, it is.  You just need to select/click under the "name" field.
Not working for, me unless I have not understood what you mean by this.

---

### Post by NadirPoint on 2016-05-31
Maybe a picture will help:

[Where to "click"]("http://stuff.is-a-geek.net/random/Thunar1.png")

---

### Post by ajgreeny on 2016-05-31
That's what I have tried without success.
In my thunar 1.6.10 it just tries, unsuccessfully, to move the top file down the list as I drag, and leaves just that single file selected.

---

### Post by kazakore on 2016-06-11
Actually that's the only place you can't start the click/drag from, [s]as I clearly mention in my first post[/s], and if you have the width to automatically resize then this can take up the whole window, or it can be hard to see which file you are starting from if the filenames are of greatly different length.

Sorry I didn't say that part above, clearly I'm getting confused with the post I made on the XFCE forum. Apologies. Still doesn't change the fact that this is the only area that it can't be done from in my experience though.

---

### Post by TenPlus1 on 2016-06-13
Is anyone else getting random crashes when ranaming files in Thunar or copy.pasting a file ??

---

### Post by 6975 on 2016-06-15
> **TenPlus1 said:**
> Is anyone else getting [COLOR=#0000ff]random crashes when ranaming files in Thunar or copy.pasting a file[/COLOR] ??
[COLOR=#0000ff]This[/COLOR] is getting old. 
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1512120](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1512120)
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1509658](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1509658)
[https://forum.xfce.org/viewtopic.php?id=9701](https://forum.xfce.org/viewtopic.php?id=9701)

Grab this ppa install from instruction & fix it(I've already test & no more crashes).
[https://lists.ubuntu.com/archives/xubuntu-devel/2016-May/011158.html](https://lists.ubuntu.com/archives/xubuntu-devel/2016-May/011158.html)

Reference:
[https://www.facebook.com/xubuntuusers/?fref=ts](https://www.facebook.com/xubuntuusers/?fref=ts)

---

### Post by ian-sproink on 2017-05-28
Going back to the original question, I hit this today when I finally upgraded to 16.04 from 14.04. Having done some digging, I'll leave this response here in case it helps some other poor, lost soul. I've also updated the (still open) bug report.

Behaviour has been deliberately changed, it seems, for "Detailed List"; it remains the same for "Icons" and "Compact List".

[This]("https://github.com/xfce-mirror/thunar/commit/bb9fe8ad3e2202be52fa5c987cb1a7744d20a0a6") is the commit in question.

In "Detailed", neither rubber-band selection (so the game of drag-a-rectangle) nor right-click-drag will work if you start them in the _first column_. Left-click-drag will pick up that file for the default move/copy action (depending on whether you're going between partitions or not); right-click-drag will just pop up the context menu.

However, if you perform the same mouse actions starting not on the name field but on _any other column_ - the size, type or date modified, etc. - then it'll do what you expect: left-click-drag will give you a variable selector, and right-click-drag will give you the copy/move/link context menu when you get the files to their destination folder/tab.

Hope that helps someone, as there'll inevitably be others wandering forlornly through Google, trying to understand what's happened.

---

### Post by Dennis N on 2017-05-28
In the detailed view, you can also just hold CTRL key down while selecting a file group with the mouse, then it will not be interpreted as dragging the first file.

---

