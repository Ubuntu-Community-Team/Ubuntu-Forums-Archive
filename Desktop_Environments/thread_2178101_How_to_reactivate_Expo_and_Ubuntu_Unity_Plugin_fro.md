---
title: "How to reactivate Expo and Ubuntu Unity Plugin from Terminal."
date: 2013-10-01
forum: Desktop Environments
---

### Post by mx6KFEh on 2013-10-01
Hello, I installed the Compiz Config Settings Manager (CCSM) to enable a 3D desktop effect. Unfortunately I deactivated Expo and Ubuntu Unity Plugin from the CCSM Desktop options list. Now I don't have the launch bar and the top bar on the desktop screen. How do I reactivate them via terminal. I can still run the terminal shortcut (ctrl+alt+t) but I do not know any other commands. 

any help will be appreciated.

---

### Post by mx6KFEh on 2013-10-01
I am running Ubuntu 12.04

---

### Post by deadflowr on 2013-10-01
Type
```
ccsm
```
from a terminal.

Added: Go to the unity plugin and re-enable it.
Select/Use the defaults for anything when prompted.
(They'll usually be highlighted)

---

### Post by mx6KFEh on 2013-10-01
Lol... the command was ccsm. I had put that above to avoid re-writing the whole thing. Love Ubuntu.

---

### Post by deadflowr on 2013-10-01
Yeah, if you've got ccsm installed that's the easy way.
A command for 12.04 to reset unity is
```
unity --reset
```
But I myself, have never had to use that.
So don't know what the results are expected to be.

Normally, in ccsm, if you think you've truly borked it up, you can go to advanced(in the side panel, and then click on the reset to defaults.
If you do that, you'll need to reset the unity plugin again.
but all the default settings for compiz will be in place.

---

