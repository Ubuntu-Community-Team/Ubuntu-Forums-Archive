---
title: "Create a custom panel applet for xfpanel"
date: 2014-09-19
forum: Desktop Environments
---

### Post by twtduck.ii on 2014-09-19
I'd like to create a custom panel applet to run java programs. I already have a java program written that simply outputs text at one line every couple seconds. Is there an easier way to do this besides writing a custom item, and if not, how do I go about writing one?

---

### Post by Toz on 2014-09-19
Have a look at the [genmon plugin]("http://goodies.xfce.org/projects/panel-plugins/xfce4-genmon-plugin"). You could use it to display info from your program. You'd need to change your app to output a line of text everytime its called, then use the genmon timer to call the program and display the info.

---

