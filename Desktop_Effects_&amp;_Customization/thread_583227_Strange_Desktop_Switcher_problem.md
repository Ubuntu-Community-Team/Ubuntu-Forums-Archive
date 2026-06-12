---
title: "Strange Desktop Switcher problem"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by iobelisk on 2007-10-20
Hi.

I have searched around and not found a thread that is similar to the issue I am having. I hope I did not miss anything.

I have Compiz Fusion installed, everything works fine. The weird thing though is off-late, when I log on to the computer, the desktop loads and everything is normal but when I use the workspace switcher on the lower panel to switch to another desktop, the cube rotates, but all panels, and icons from the desktop are gone. The computer is working fine, nothing is hung, I just cannot seem to get the panels back. So I cltr alt bksp, log back on, continue working on one window, when some time passes, i try switching desktop, and yep, its all good. its weird. the problem is very inconsistent in the sense that you never know if a ctrl alt bksp is going to fix it. i have noticed if i wait a while after logging on and before switching desktop, usually it is okay. Oh btw, and all this while if i use cltr alt arrow to switch desktop, its not a problem. its only when i click on the workspace switcher on the panel when everything disappears. Also, when the desktop switcher does work, it does not flip a cube, it just switches in "normal mode".

I thought maybe something was conflicting within my compiz plugin settings. so i went and had a look but did not really fnd anything, but i did turn off all plugins that i don't really need. I wonder if somebody has had this problem before? It would be great to be able to resolve this. Thank you.

---

### Post by sunny_nwho on 2007-10-21
same here. for the cube does not rotate either

---

### Post by moaxey on 2007-10-21
I assumed that each 'desktop' has its own set of icons now...

I am having trouble with desktop cube - all the viewport switching extensions...

Compiz-fusion seems to just ignor the setting i have for 4 desktops, and i just have the two basic gnome ones, and no way to switch between them except for what would seem to be the old-fashioned (pre-beryl) way from ubuntu 6.10...

tried commands from this thread: [http://ubuntu-tutorials.com/category/compizberyl/](http://ubuntu-tutorials.com/category/compizberyl/)
```
gconftool-2 –type int –set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 –type int –set /apps/compiz/general/screen0/options/number_of_desktops 1
```

which didnt seem to do anything...

---

### Post by wetear on 2007-10-22
It seems that the problem is solved. I used  **gconf-editor** to change the keys mentioned in the code:

```
/apps/compiz/general/screen0/options/number_of_desktops is set to 1
/apps/compiz/general/screen0/options/hsize is set to 4
```

And desktobe cube is ok again.

---

### Post by rowinggolfer on 2007-10-24
I had the same problem (when I used desktop-switcher, I would lose all taskbars, and be unable to switch back).
Problem solved thanks to this forum.
I opened gconf-editor, then changed the apps/compiz/general/screen0/options number_of_desktops from 4 to 1.  

BTW - I think these desktop effects are very impressive!

---

### Post by swmmng on 2007-10-24
I had the exact same problem, and this solution nailed it.  Thanks.

---

