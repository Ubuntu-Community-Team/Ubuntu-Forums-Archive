---
title: "A couple of problems with Unity - Any ideas ?"
date: 2011-11-17
forum: Desktop Environments
---

### Post by Ithacan on 2011-11-17
Has anyone encountered these problems, and do they have any solutions?

1) Have an older software package that uses X-windows dialogues. In Unity (Ubuntu 11.10) it calls small pop-up confirmation windows such as "are you sure you want to close this window?" In unity you can't just click "OK" I have to click on another open window elsewhere (say a terminal) and then click back to the dialogue box before I can click the "OK"

2) As a work around I installed Gnome, but even though I did everything to install the Gnome desktop - when I select it (from the little gear symbol) at login and then click logon, unity activates anyway and ignores my choice. 

Any help would be appreciated.

---

### Post by stinkeye on 2011-11-17
Don't know why unity loads in the gnome session.
Are you using fusion-icon in startup?
If compiz is loading as your window manager you will have unity as it is a plugin for compiz.
 
If gnome-shell (which is all you need to install for the gnome session choice at login) is installed you should be able to change with alt+F2
```
gnome-shell --replace
```

With the change from gnome2 to gnome3 I'm not
quite sure what you are installing.

---

### Post by Ithacan on 2011-11-17
gnome-shell --replace is a good work around. 

And unity --replace gets me back to unity for everything else. 

Thank you - this works perfectly and kills the two birds with one stone...

---

### Post by stinkeye on 2011-11-17
OK, but mutter should be loading as your window manager in the gnome session
not compiz.

---

