---
title: "Ctrl+C doesn't always work"
date: 2006-06-18
forum: Desktop Environments
---

### Post by [S|G] on 2006-06-18
Title pretty much says it all. It's an issue I've been having for as long as I can remember using linux. Sometimes I select, ctrl+c and then ctrl+v and everything is fine. Then sometimes I can't paste.

I though about always using ctrl+x. Same happens. How come what I copy simply vanishes? And I can't even tell you how to reproduce it, it's completely random. Some times it works, some times it doesn't.

It is a minor bug that has been slowly making me mad. Anyone has also experienced this? Is there any way to fix it?

---

### Post by raffytaffy on 2006-06-18
Ive come across this issue also...not to often...its not only you...as to a solution....*shrugs*

---

### Post by nadeldave on 2006-06-18
My experience with this problem is that its more reliable to Control C to copy and  use Shift+Insert to paste.  Seems to work 99%, if not all of the time.

---

### Post by raptros-v76 on 2006-06-18
you cant use ctr+c to copy stuff in a terminal because thats already bound to sigkill.  and ctrl+v and ctrl+x dont work for similar reasons

---

### Post by [S|G] on 2006-06-18
Just to clarify things: it wasn't in a terminal

---

### Post by aysiu on 2006-06-18
In KDE and Gnome and XFCE, the clipboard gets emptied when you close the source application... *unless* you're running something like *gnome-clipboard-daemon* or *clipper*.

**So this will work:**
Highlight text in Firefox. 
Control-C it.
Open Gedit.
Control-V it.

**This will *not* work:**
Highlight text in Firefox
Control-C it.
Close Firefox.
Open Gedit
Control-V it.

---

### Post by [S|G] on 2006-06-19
Thanks a LOT for that :) I never noticed that in years using linux >.< Guess I always dismissed it as a "minor bug" and never tried to discover its cause.

Just another doubt now: is that a bug or a "feature"?

---

### Post by aysiu on 2006-06-19
I call it a bug. Some people might call it a feature.

I see no logical reason why the clipboard should be cleared when you close an application--I thought that was the whole point of a clipboard, to remember what you copied.

People are usually pretty vague when they say "Windows is more user-friendly than Linux." I don't agree with the statement overall, but I think this is one particular example that Windows wins hands-down on.

---

