---
title: "double click to roll up and icon lable background"
date: 2012-05-20
forum: Desktop Environments
---

### Post by bug67 on 2012-05-20
Loving Xubuntu 12.04.  Very functional/tweakable.  Can't seem to figure out 2 things:

1.  When I double click on the title bar of an open window, it will not roll up.  I have "Shade Window" selected in Settings>Window Manager>Advanced>Double click action.
[IMG]http://bug67.smugmug.com/Computers/Linux/Xubuntu/i-v488Gfx/0/M/Screenshot-02-M.png[/IMG]

My other minor issue is, how do I remove the icon title background and change the font color for desktop icons?  I'd like to remove the gray background and change the font color from black to, let's say, white or a light gray.
[IMG]http://bug67.smugmug.com/Computers/Linux/Xubuntu/i-WTSJBpz/0/Th/Screenshot01-Th.png[/IMG]

Using Xubuntu 12.04 x64 with xfce 4.10.

Thanks in advance.

---

### Post by ajgreeny on 2012-05-20
I am not sure I can help with the first problem, other than asking if you have logged out and in again, as that may be necessary.

For the second question about desktop icons the attached file may help.  Save it in your home and rename it **.gtkrc-2.0**.  Now reboot or maybe just logout and in again to see if it works.  It definitely worked in Xubuntu 11.04, but my uncertainty is with the version of gtk and whether it is now .gtkrc-3.0 that is needed instead of .gtk-2.0.

Just about to try and will let you know asap.

---

### Post by bug67 on 2012-05-20
> **ajgreeny said:**
> I am not sure I can help with the first problem, other than asking if you have logged out and in again, as that may be necessary.
Logged in/out many, many times.  No affect.

> For the second question about desktop icons the attached file may help.  Save it in your home and rename it **.gtkrc-2.0**.  Now reboot or maybe just logout and in again to see if it works.  It definitely worked in Xubuntu 11.04, but my uncertainty is with the version of gtk and whether it is now .gtkrc-3.0 that is needed instead of .gtk-2.0.

Just about to try and will let you know asap.

Not sure what you're telling me to do here.  I'll wait and see what you come up with before I try anything.

---

### Post by ajgreeny on 2012-05-20
Sorry, but like an idiot, I forgot to attach the file I spoke of, so here it is now.  I have tested it out and it works fine in Xubuntu 12.04.

Open it in your text editor (leafpad?) and save it to your home folder named as **.gtkrc-2.0**

Don't forget the . at the start of the file name or it will not work.  Now logout and in again and the icon labels will only show a highlight background when selected, and label text will be white when not selected, and green when selected, though the green is showing blue for some reason in the screenshot which I have also attached.

I have also tried the window shading and it does not appear to work on my system either in Xubuntu 12.04.

---

### Post by bug67 on 2012-05-20
> **ajgreeny said:**
> [COLOR="Green"]green[/COLOR] when selected

Any way to change this?  I'd rather the letters stay white but *have* the gray background when highlighted.

Worked like a charm by the way.  Thanks!  :cool:

I bet there's a way to do this kind of stuff with this thing but I'm cluless:
[IMG]http://bug67.smugmug.com/Computers/Linux/Xubuntu/i-k2Rjq2d/0/M/Screenshot-03-M.png[/IMG]

---

### Post by ajgreeny on 2012-05-20
Yes, you can change the text colours by editing the part of the file at lines 28-30 in the file
```
fg[NORMAL] = "#ffffff"        #this is white
fg[SELECTED] = "[COLOR=Black]#00ff00[/COLOR]"      # this is green
fg[ACTIVE] = "#0000ff"        # this is blue
```
Change the [COLOR=Black]#00ff00[/COLOR] shwn to #ffffff like the line above and text will remain white even when selected.

PS: In spite of my last post comments, window shading does work now on mine after a logout and in again.

---

### Post by rai4shu2 on 2012-05-20
If double-click is problematic (and it usually is), go to Settings/Settings Manager/Mouse and Touchpad/Behavior and bump up the Double Click Time (300 or 400 ms seems about right for a normal mouse).

---

### Post by bug67 on 2012-05-20
> **ajgreeny said:**
> Yes, you can change the text colours by editing the part of the file at lines 28-30 in the file
```
fg[NORMAL] = "#ffffff"        #this is white
fg[SELECTED] = "[COLOR=Black]#00ff00[/COLOR]"      # this is green
fg[ACTIVE] = "#0000ff"        # this is blue
```
Change the [COLOR=Black]#00ff00[/COLOR] shwn to #ffffff like the line above and text will remain white even when selected.

PS: In spite of my last post comments, window shading does work now on mine after a logout and in again.
Perfect!  :cool:

> **rai4shu2 said:**
> If double-click is problematic (and it usually is), go to Settings/Settings Manager/Mouse and Touchpad/Behavior and bump up the Double Click Time (300 or 400 ms seems about right for a normal mouse).
420 ms did the trick!  :cool:

Thanks!  :D

---

