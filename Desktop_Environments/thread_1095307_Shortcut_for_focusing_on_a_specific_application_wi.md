---
title: "Shortcut for focusing on a specific application window"
date: 2009-03-13
forum: Desktop Environments
---

### Post by danielaharon on 2009-03-13
Hi,

Is there a way to define a shortcut for specific application windows? 

Here's the scenario: I usually work with the same set of applications: Eclipse, Firefox, gedit, terminal, etc. and I'd like to use keyboard shortcuts to quickly switch to any of them (e.g., use Mod4+E to switch to the existing Eclipse window or Alt+F to switch to the existing Firefox window). I know I can use gconf-editor to launch a new instance of applications but that's not what I need. I need to just bring a specific existing window to focus.

Thanks in advance!
Daniel

---

### Post by danielaharon on 2009-03-14
Assuming from the lack of response that there is no "built-in" way to accomplish what I described below, are there other tools/packages that provide such functionality?

Thanks,
Daniel

---

### Post by zhocchao on 2009-03-14
u can use wmctrl. 

wmctrl -a "Firefox"

xbindkeys for the shortcuts

---

### Post by danielaharon on 2009-03-14
Awesome!

Many thanks,
Daniel

---

### Post by shinyblue on 2011-01-05
:guitar: you rock! wmctrl EXACTLY what is missing from compiz...

wmctrl -a firefox || firefox &

---

