---
title: "Way for script to learn which workspace is displayed?"
date: 2009-06-23
forum: Desktop Environments
---

### Post by tauchris on 2009-06-23
Is there any way that a script can determine which desktop workspace is currently being displayed?  I want to have a launcher on my main panel that will open a terminal window in a different starting directory, depending one which workspace I'm viewing when I click the launcher.  So far, I haven't found any way to do that.  Does anyone have a suggestion?  Chris

---

### Post by zhocchao on 2009-06-23
this gives you the number (0=1). Does not work in compiz (i think)

wmctrl -d |grep "*"|awk '{print $1}'

---

### Post by tauchris on 2009-06-23
What is "wmctl"?  What package is that part of?  It doesn't appear on my Ubuntu system, and it doesn't show up in Synaptic anywhere, either...

---

### Post by zhocchao on 2009-06-23
you can install it with sudo apt-get install wmctrl

---

### Post by tauchris on 2009-06-23
Yeah, so thanks for the pointer.  Does not appear to work correctly on compiz.  :-(  Thanks anyway.  Any other (more portable) suggestions?

---

### Post by zhocchao on 2009-06-23
with xmousepos(xmousepos |awk '{print $1}') (package xautomation) you can determine the position of your mouse. As you have one great desktop in compiz e.g. 4*1280x800 = 5120x800. x-Position 2000 would be workspace(or viewport?) 2.

---

### Post by tauchris on 2009-06-24
Thanks!

---

