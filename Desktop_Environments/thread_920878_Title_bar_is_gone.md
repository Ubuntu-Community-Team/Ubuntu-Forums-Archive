---
title: "Title bar is gone"
date: 2008-09-15
forum: Desktop Environments
---

### Post by Guyon on 2008-09-15
I'm not at all sure why this happened. I've rebooted with no luck. Sorry I can't give you much detail, as I'm completely clueless about this issue. Please be detailed, for I am completely new.

ubuntu 8.04

Problem solved by switching to Metacity, thanks Brian.

---

### Post by Brain-free on 2008-09-15
I take it you have compiz enabled. If you do, try this.

Type at terminal
```
sudo apt-get install fusion-icon
```

This installs an application that manages your compiz easily. After it is installed, run it. It should be in Application -> System Tools -> Compiz Fusion Icon. 

It should now appear on the top of your desktop in the right. Right click on it to show the menu and then click "Reload Window Manager".

If this is not working try "Select Window Manager" -> Metacity

---

