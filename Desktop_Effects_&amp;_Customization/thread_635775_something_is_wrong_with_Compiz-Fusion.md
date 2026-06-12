---
title: "something is wrong with Compiz-Fusion"
date: 2007-12-09
forum: Desktop Effects &amp; Customization
---

### Post by Bandicoot on 2007-12-09
I've been using Compiz Fusion for about a week now, everything was fine until today. All my applications start at the top of the screen and the top border (with the min/maximize buttons) is not visible. With a lot of work I can get it visible ( resizing the widow a lot of times sometimes helps). When I switch to the gconf configuration backend everything is fine, but as soon as I switch to flatfile configuration backend the problem is back again. I have windows decoration turned on and also the workaround plugin (not using it makes no difference). Anybody knwos what's causing this ?? I've enclosed a screenshot to show what I mean.

---

### Post by Ub1476 on 2007-12-09
Are they gone or just behind the panel? You can press alt+click anywhere on the window to drag it around.

If they are gone, try to run:

```
compiz --replace
```

---

### Post by Bandicoot on 2007-12-09
No, they are not gone. Dragging does give me my top border back, but it is very annoying that every app/window starts at the top off the screen and I have to drag it to have my borders visible again.. Maybe it's some sort of setting but I can't figure out which one it is, I've tried disabling/enabling almost every plugin that may have something to do with this strange behavior but to no avail ..

---

### Post by Ub1476 on 2007-12-09
Alright, here's a small fix:

Open Advanced Desktop Effects>Window Managment>Place Windows>Set placement mode for what works for you.

---

### Post by Bandicoot on 2007-12-09
Ok, thanx that solves my problem ! I'm still puzzled though why this behavior suddenly happened, it was okay before.

---

### Post by Ub1476 on 2007-12-09
Well, we're still on v. 0.52 of Compiz here I believe, so strange things happen:P

---

