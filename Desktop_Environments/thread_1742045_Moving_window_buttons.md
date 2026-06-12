---
title: "Moving window buttons"
date: 2011-04-28
forum: Desktop Environments
---

### Post by TNAFan on 2011-04-28
Trying to move window buttons on the "window buttons" panel like you can do on Ubuntu by default and Kubuntu(after changing a few options).  Cannot figure out how to do this.  Can anyone help me with how to do so?

Xubuntu 11.04

---

### Post by 3Miro on 2011-04-28
Application -> Settings -> Settings Manager -> Windows Manager. Check the themes, some themes allow for customization of the windows buttons, others don't. You can install more xfwm4 themes from either the Software Center/Synaptic Package Manager or you can go to  [http://xfce-look.org/](http://xfce-look.org/)

---

### Post by slooksterpsv on 2011-04-28
[http://ubuntuforums.org/showthread.php?t=1704596](http://ubuntuforums.org/showthread.php?t=1704596)

So you go to Applications menu -> Settings -> Settings Manager -> Window Manager

And there's an area in there where you can drag and drop your button layout.

---

### Post by TNAFan on 2011-04-28
You misunderstand.  Not the ones on the individual windows.  I mean the buttons on the task bar.

---

### Post by slooksterpsv on 2011-04-28
> **TNAFan said:**
> You misunderstand.  Not the ones on the individual windows.  I mean the buttons on the task bar.

Right-click on the icon, choose move, and drag it to where you want it.

---

### Post by TNAFan on 2011-04-28
Tried that.  That just moves the window.

---

### Post by TNAFan on 2011-04-28
Perhaps if I attach a picture I can help explain.  The circled icons is what I want the ability to move.  Like in Ubuntu (previous to Unity).

---

### Post by slooksterpsv on 2011-04-28
> **TNAFan said:**
> Perhaps if I attach a picture I can help explain.  The circled icons is what I want the ability to move.  Like in Ubuntu (previous to Unity).

Oh so not the actual application icons, but the currently open application window list, that I do not know how to move.

---

### Post by TNAFan on 2011-04-28
When you attempt to, they lift up, like it is possible, but when you try to put them where you want them they just go back to their original spots.

---

### Post by Copper Bezel on 2011-04-28
There's a little row of dots at the far left of the list. Right click that, and there's an option for "move"; you could also instead "remove" the task selector and "add" it where you want it. (Exactly as in Gnome, for those curious.)

---

### Post by 3Miro on 2011-04-28
The old xfce panel (4.6) could adjust the order of the windows. I think that feature got lost when they rewrote everything for 4.8.

So the answer is: I don't think you can.

---

### Post by Peadogie on 2011-04-29
In Xfce 4.8 right click anywhere in the panel, Panel>Panel Preferences...>Items. Select  the Item you want to move and use the arrows to move it.

Ooops:oops:, I think you're wanting to move the individual window buttons. As 3Miro said I don't think you can.

---

### Post by n0c0d3 on 2011-05-09
Where can I complain about this omission? Not being able to sort the buttons manually is pretty annoying. It's not really like an improvement to leave it out in an upgrade imho.

---

### Post by HobbitTR on 2011-05-13
> **n0c0d3 said:**
> Where can I complain about this omission? Not being able to sort the buttons manually is pretty annoying. It's not really like an improvement to leave it out in an upgrade imho.

Settings -> Settings Manager -> Window Manager -> Button Layout (R Column) Drag the maximize, minimize, close and menu buttons where you want them.

This forum game me the hint how to do this. Thanks :D

---

### Post by n0c0d3 on 2011-05-13
Hi HobbtTR,

I think you didn't read the thread and what the OP meant. It's NOT about the 'close', 'minimize' etc. buttons, but about being able to manually move/sort the window-buttons on the window-buttons item/plugin on  the panel (in Windows this is the taskbar)

Thanks anyway ;)

---

### Post by HobbitTR on 2011-05-16
> **n0c0d3 said:**
> Hi HobbtTR,

I think you didn't read the thread and what the OP meant. It's NOT about the 'close', 'minimize' etc. buttons, but about being able to manually move/sort the window-buttons on the window-buttons item/plugin on  the panel (in Windows this is the taskbar)

Thanks anyway ;)

Yes you are correct, my bad, I apologize :(

---

### Post by gsmanners on 2011-05-16
This is a known issue. See:

[Manual sorting of Task List not possible]("https://bugzilla.xfce.org/show_bug.cgi?id=7058")

---

### Post by n0c0d3 on 2011-08-07
The corrected version with a working sorting option can be downloaded from here (bottom of page):

[http://packages.ubuntu.com/oneiric/xfce4-panel](http://packages.ubuntu.com/oneiric/xfce4-panel)

---

