---
title: "Keyboard shortcuts and workspace switching gone bonkers."
date: 2014-05-01
forum: Desktop Environments
---

### Post by russo.mic on 2014-05-01
So, as of 14.04 clean install, for some reason control+alt+arrow doesn't change my workspaces anymore.  It's super annoying.  Also, I can't use CCSM anymore.  I've tried setting the shortcut there, and in the keyboard settings shortcut app within ubuntu.  And when I use the application switcher, it won't switch workspaces if I pick an app that is in a different workspace. What gives?  Thanks!

---

### Post by grumblebum2 on 2014-05-01
On a default install of Trusty I think you only have the one workspace.
Right click on desktop > change desktop background
Go to the behaviour Tab and enable workspaces.

If you think something you did in ccsm messed it up, in the terminal run...
```
dconf reset -f /org/compiz/
```
Then log out and back in and enable workspaces as above.

---

