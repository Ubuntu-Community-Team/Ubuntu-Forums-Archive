---
title: "Disappearing icons..."
date: 2013-04-24
forum: Desktop Environments
---

### Post by Rtedmonston on 2013-04-24
I don't know what happened but it seems like every time I log into Ubuntu, more of my default program icons have gone and been replaced by a blank file folder? Does that make any sense? Where can I find them so I'm not confused to all hell when I want to open terminal or Synaptic?

---

### Post by Frogs Hair on 2013-04-24
You can reset the icons to default , but you will have to add your most used applications again. If that fails reseting unity may help.
```
unity --reset-icons
```12.04 ```
unity --reset
```12.10```
setsid unity
```

---

### Post by Rtedmonston on 2013-04-25
Nope, Trying that I get: WARN  2013-04-25 10:53:50 unity.launcher LauncherIcon.cpp:433 Unable to load 'utilities-terminal' from icon theme: 


It's as if several system icons were deleted?

---

### Post by Frogs Hair on 2013-04-25
When you see a question ? it can indicate the path to the image is has been disrupted for some reason and it's not likely you moved icons to a new folder. Check ask Ubuntu there sre some similar posts but not identical.

---

