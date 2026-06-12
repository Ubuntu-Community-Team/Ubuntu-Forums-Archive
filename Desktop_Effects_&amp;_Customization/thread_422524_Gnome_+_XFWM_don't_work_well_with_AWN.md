---
title: "Gnome + XFWM don't work well with AWN"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by TheTux on 2007-04-25
Hi.

I've changed my default window manager to xfwm because I like it's behaviour and it has a stable compositor. I don't want to use compiz/beryl because I just need a compositor to make my desktop more responsive without the fancy effects. But xfwm does not seem to run well with avant window navigator. AWN only appears on the workspace where I started it. I can run another AWN on another workspace it is quite ridiculous to run it on every workspace. Another thing is, if I maximize the window of an application, the horizontal scroll bar won't work. I cannot drag the bar. 

Does anybody knows how to solve this as I have searched in this forum and found out that most AWN users run compiz or beryl.

Please help. Sorry for my English.

---

### Post by josephus on 2007-04-25
you can use wmctrl or devil's pie to set AWN as a sticky window.  Both of these programs are available in the repositories.

---

### Post by TheTux on 2007-04-25
Thanks for the quick reply. Devilspie solved the first problem. For those who also has the same problem, Here's how I done it, based on the documentation:

first install devilspie
```

apt-get install devilspie

```

Then create a configuration( .ds ) file in ~/.devilspie/
for example I created avant.ds file so that would be ~/.devilspie/avant.ds

put this in the file:
```

(if (is (application_name) "avant-window-navigator" ) (stick))

```

now you can run devilspie, to make it start everytime you login, add to gnome-session-properties

Ok done with that

Now, the second problem is the horizontal scrollbar won't move if I drag it using mouse. But I can move it using arrow keypad. Anyone?

---

### Post by josephus on 2007-04-25
I think the problem is that all the mouse events near the bottom of the screen is intercepted by AWN and therefore the program beneath it is unable to detect the mouse click needed to move the horizontal scrollbar.  I doubt that there is an easy fix to this problem, and you'll probably need to file a bug report with the developer in order to resolve this.

---

