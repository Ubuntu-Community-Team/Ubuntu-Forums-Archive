---
title: "PekWM - AutoProperties questions"
date: 2008-10-09
forum: Desktop Environments
---

### Post by Gorgamel on 2008-10-09
A) I'm trying to get programs to start at a specific position and size, but they don't seam to agree.
The following should (at least if I decide) put aterm windows in a group and also have them in the size of 80x18 at X:200 Y:200. This doesn't work at all. No group, no size, no position. Any idea on what's wrong? The group property works fine for FF.

```
Property = "aterm,XTerm" {
ApplyOn = "Start New"
Group = "term" {Size = 0 }
FrameGeometry = "80x18+200+200"
}
```
I have also tried with ClientGeometry, but still no result.


B) When opening Pidgin, I want it do start at workspace 2 with:
```
Property = "^pidgin,^Pidgin" {
ApplyOn = "Start New"
Workspace = "2"
}
```
But starts in workspace 1


C) Another question: would it be able to show the title bar on on the active window/only the not active windows?
Just an idea I had to see if it would be possible :)

That would be all for now ;)

---

### Post by Gorgamel on 2008-10-14
Bump

---

