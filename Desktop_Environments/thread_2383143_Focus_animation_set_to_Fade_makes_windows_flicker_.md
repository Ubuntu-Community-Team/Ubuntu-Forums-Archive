---
title: "Focus animation set to Fade makes windows flicker when focused"
date: 2018-01-21
forum: Desktop Environments
---

### Post by checoimg on 2018-01-21
I've been playing with Compiz and now I want to set a focus animation and I prefer the fade animation for this but it causes the windows to flicker. I read a bug about it and in the comments from 2008 they mention something about the focus animation having a fade effect by default, and these are conflicting causing the flicker.

This are the settings for the focus animation in CCSM:

```
(type=Normal | Dialog | ModalDialog | Utility | Unknown) & !(name=compiz)
```

In conclusion what I want is a slow fade animation when a window is focused.

This is a video of the bug: [VIDEO]("https://youtu.be/0awlKwX6rcE")

And the bug report: [REPORT]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1741704")

---

