---
title: "Store windows on different desktops?"
date: 2008-02-02
forum: Desktop Effects &amp; Customization
---

### Post by eindbaas on 2008-02-02
I just installed Gutsy on my machine here for the first time, and really enjoying the smoothness and responsiveness of the effects of compiz. I'm using 4 desktops and what i am wondering is: can i make it happen that a few programs are automatically started when i login and placed on desktops (maybe even in a certain position)?

For example, i usually have my system monitor running on desktop 2 and would be very pleased if that thing just stayed there if i restart my computer.

---

### Post by BennBuntu on 2008-02-02
I just tried the "Remember currently running applications" in session options, but they seem to all end up on desktop 1.

I seem to remember XFCE window manager remembering where they were, you can try it on your exisiting install.

```
sudo apt-get install xubuntu-desktop
```


Anther option is to use hibernate or suspend instead of shutting down.

---

### Post by eindbaas on 2008-02-02
Hmm, the hibernation sounds like a good alternative. Thanks for the help!

---

### Post by aroch1 on 2008-02-02
In compizconfig-settings-manager look under the "Place Windows" plugin for the "Windows with fixed viewport" area.  You can enter a rule that will match your window here...the matching syntax is detailed [here]("http://wiki.compiz-fusion.org/WindowMatching").  To start the program automatically when you log on, go to Preferences->Sessions and add it to the start up programs list.

---

