---
title: "Getting the &quot;minimize, maximize and exit&quot; buttons while using beryl"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by Scubastev013 on 2007-06-28
Hey everyone.  Sorry if this has been answered elsewhere, I couldn't find it.  I would like to use beryl, but I keep finding that when I use the beryl window manager, I lose the buttons on the top right of the screen that minimize, maximize and close the open window.  I have this under the metacity window manager.  Is there any way I can fix this?  I believe it worked before, but not now.  I didn't change anything.  Please advise and thanks in advance in advance for your help!!!


Scuba

---

### Post by speaker219 on 2007-06-28
> **Scubastev013 said:**
> Hey everyone.  Sorry if this has been answered elsewhere, I couldn't find it.  I would like to use beryl, but I keep finding that when I use the beryl window manager, I lose the buttons on the top right of the screen that minimize, maximize and close the open window.  I have this under the metacity window manager.  Is there any way I can fix this?  I believe it worked before, but not now.  I didn't change anything.  Please advise and thanks in advance in advance for your help!!!


Scuba
run in terminal:
```
gtk-window-decorator --replace
```

---

### Post by Scubastev013 on 2007-06-28
Running that in my terminal didn't do anything.  What should I do next?

---

### Post by LouisvilleLIP on 2007-06-28
If I run gtk-window-decorator --replace in terminal and then leave that terminal window open, it fixes the problem.  Closing the terminal window causes compiz to revert back to no min/max/close buttons/borders.

---

### Post by Scubastev013 on 2007-06-28
I'm still having the same problem.  Even if I run that command, I still don't get the top  row of information (minimize/maximize/quit)  Is this something that happens a lot?  What should I do about it.  I could turn off beryl, but its SO COOL!

---

### Post by speaker219 on 2007-06-28
Press Alt+F2 and type "gtk-window-decorator --replace" and hit enter.

---

### Post by mpneerkaje on 2007-06-29
I too had the same problem, I think its the problem with the GLX, but i do not know how to solve this. when i used the similar command, i got the folowing error:

[COLOR="Red"]compiz --replace&[/COLOR]
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
inotify_add_watch: No such file or directory
[COLOR="Red"]
emerald --replace&[/COLOR]
No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32


Any solution?

---

### Post by bake7221 on 2007-06-29
> **Scubastev013 said:**
> Hey everyone.  Sorry if this has been answered elsewhere, I couldn't find it.  I would like to use beryl, but I keep finding that when I use the beryl window manager, I lose the buttons on the top right of the screen that minimize, maximize and close the open window.  I have this under the metacity window manager.  Is there any way I can fix this?  I believe it worked before, but not now.  I didn't change anything.  Please advise and thanks in advance in advance for your help!!!


Scuba

If you are having a problem with just the "buttons" and not the borders than I'm not sure what to do ... I use an Nvidia 8800GTS forced AIGLX, and when I first installed Beryl, the borders disappeared ... the way to fix this is to visit this site, it'll explain ... 

[http://nlindblad.org/2007/01/28/no-window-borders-with-beryl-and-nvidia-aiglx/](http://nlindblad.org/2007/01/28/no-window-borders-with-beryl-and-nvidia-aiglx/)

---

### Post by Mr Greencastle on 2007-06-29
I used to run into this problem whilst using Beryl, I found it was just a glitch for me. I fixed it by minimizing the applications then unminimizing.

One solution is to install Emerald as the window decorator:
sudo apt-get install emerald emerald-themes

You can right-click the Beryl logo and switch your window decorator to Emerald. There is also a new manager where you can find themes, new ones can be found at
[www.gnome-look.org](www.gnome-look.org) (under the Beryl tab)

Running this command in your startup to make it default:
emerald --replace

Another would be to try Compiz Fusion (which has many of Beryl's features and some new ones)
There are many threads explaining how to do this.

Good Luck!

Mr Green

---

### Post by Angry Dragon on 2007-10-12
> **LouisvilleLIP said:**
> If I run gtk-window-decorator --replace in terminal and then leave that terminal window open, it fixes the problem.  Closing the terminal window causes compiz to revert back to no min/max/close buttons/borders.



Try going to system -> preferences -> sessions and then add gtk-window-decorator --replace to startup programs. I was having the same problem and this worked for me.

---

