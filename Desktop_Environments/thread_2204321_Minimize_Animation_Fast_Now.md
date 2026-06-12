---
title: "Minimize Animation Fast Now"
date: 2014-02-07
forum: Desktop Environments
---

### Post by Brandon_MacEachern on 2014-02-07
Since updating Ubuntu about a few days ago, minimize animations now happen in a snap, and not that smoother slow animation it used to.

How can I get the smoother slow animation back?  I liked it.

---

### Post by stinkeye on 2014-02-07
Unity has a a slow minimize animation for the first 100 times you minimize then it speeds up.
This is supposed to let new users see were the minimized window is going.

In dconf there are settings for before you reach the 100 minimize threshold and after.
If you like the slow animation you can set these to be the same.
Change the dconf setting, **com.canonical.Unity minimize-fast-duration**
You can do this in **dconf-editor** (may need to install)
[ATTACH=CONFIG]250177[/ATTACH]

or 
in the terminal run....
```
gsettings set com.canonical.Unity minimize-fast-duration 800
```

---

### Post by Brandon_MacEachern on 2014-02-08
> **stinkeye said:**
> Unity has a a slow minimize animation for the first 100 times you minimize then it speeds up.
This is supposed to let new users see were the minimized window is going.

In dconf there are settings for before you reach the 100 minimize threshold and after.
If you like the slow animation you can set these to be the same.
Change the dconf setting, **com.canonical.Unity minimize-fast-duration**
You can do this in **dconf-editor** (may need to install)
[ATTACH=CONFIG]250177[/ATTACH]

or 
in the terminal run....
```
gsettings set com.canonical.Unity minimize-fast-duration 800
```
Perfect, thanks!

---

