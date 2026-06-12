---
title: "Windows no longer rollup when double-clicked"
date: 2007-02-03
forum: Desktop Environments
---

### Post by rphelps on 2007-02-03
I am no longer able to rollup any windows on my desktop even though on the "windows preference" dialog the titlebar action is set to "rollup" 

Is there a configuration file somewhere that I can edit? Or do I have to do something drastic like kill my userspace and redo it?

---

### Post by gradedcheese on 2007-02-04
It's actually a setting you can edit in gconf.  To do it, run:

gconf-editor

Go to apps->metacity->general

It's the first option (action_double_click_titlebar) and you can choose from toggle_maximize and (what you want), toggle_shade

---

### Post by rphelps on 2007-02-04
I fixed my problem. I had been messing with the mouse settings and set the "mouse double-click timeout" option to 100mSec. I was not able to double click fast enough to make things work.

---

