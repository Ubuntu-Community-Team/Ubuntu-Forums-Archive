---
title: "Moving files from folders to desktop makes a copy"
date: 2009-04-18
forum: Desktop Environments
---

### Post by aldolat on 2009-04-18
Hi all,

I just upgraded to Jaunty from Intrepid and noticed a strange issue, never seen before.

**The problem**
When I drag a file/folder from any folder to the desktop, I make a copy of that file/folder. So, I have to hold down Shift to simply move that file to the desktop.

**Info**
[LIST]
[*]I use Compiz, but either with Compiz enabled or not, I have this issue.
[*]I tried to search into gconf-editor for a possible preference related to this behaviour, but found nothing.
[*]If I create a new test user (with default preferences), this problem is not present (I can drag and drop files to desktop without making a copy, as expected).
[*]Dragging a file from a folder to one other results in moving it, not copying (as expected).
[/LIST]

What could be the possible reason?

---

### Post by aldolat on 2009-04-18
**[Update]**

In gconf-editor/apps/nautilus/desktop/ I enabled the option: network_icon_visible (but I could enable another option among them). The issue disappeared. Now I can move files & folders to the desktop as expected.

To test again, I logged out and relogged in: the issue is back again.

What do you think about?

---

