---
title: "startup application windows under menu bar"
date: 2008-07-10
forum: Desktop Environments
---

### Post by kholburn on 2008-07-10
I have one or two applications I like to start up when I log in.  They seem to start up before the menu bar therefore they appear under the menu bar.  I can't access the window title bar to move them.  Now whenever I start up I have to move them from under the menu bar using the move function from the task bar.  How can I stop this from happening?

---

### Post by skip mcshwang on 2008-07-10
You could try holding "alt" and then clicking anywhere in the window to drag it

---

### Post by kholburn on 2008-07-14
> **skip mcshwang said:**
> You could try holding "alt" and then clicking anywhere in the window to drag it

Yeah, that makes it easier but I'd prefer it if the windows didn't end up there in the first place.  

Perhaps they are starting up before the menu bar and perhaps waiting to start them up until the menu bar had started up would work.  

How do I do that?  A startup script?  But I would have to rewrite it every time I wanted to change my startup programs or their geometry.

---

### Post by Tr10 on 2009-05-11
> **kholburn said:**
> Yeah, that makes it easier but I'd prefer it if the windows didn't end up there in the first place.  

Perhaps they are starting up before the menu bar and perhaps waiting to start them up until the menu bar had started up would work.  

How do I do that?  A startup script?  But I would have to rewrite it every time I wanted to change my startup programs or their geometry.

I have this same problem, and I would love a simple way to fix it, there must be a way to tell ubuntu the cordinates to put a new window at.

EDIT: After closely looking at the settings of my window manager, I found a way to do this.
I use CompizConfig Settings Manager w/ gnome

I opened CompizConfig and went to the window section.
Clicked on put, clicked on the misc-options tab, clicked on the right arrow for padding, added 25 pixels of padding to the top, then clicked enable and back and then closed the window, and it worked amazingly.

Goes to show how easy this was, I was just looking in all the wrong places. :P

Cheers.

---

