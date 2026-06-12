---
title: "Applications with no edges...."
date: 2012-07-09
forum: Desktop Environments
---

### Post by piloti on 2012-07-09
[SOLVED] Not sure how to describe this, but in the last week or so most of the applications I am using seem to have lost their borders.
This includes the maximise / minimise and x to close. 
They have also lost their header bar/ top bit which allows you to move non maxmises applciations around the screen.
As an example, now I have VLC open. It plays correctly, but once it is open, I can not move it around the screen; it stays where it opens.
Sorry this is a poor descripotion, but this is the best way I can describe what is happening.
ANy clues, or is this part of Ununtu integrating things into the new desktop environment. 
I am using 12.04 LTS.

---

### Post by ajgreeny on 2012-07-09
Install compizconfig-settings-manager if you do not already have it and make sure window-decoration plugin is enabled.

If that is no help you can reset unity and compiz to their defaults with
```
gconftool-2 --recursive-unset /apps/compiz
unity --reset
```

---

