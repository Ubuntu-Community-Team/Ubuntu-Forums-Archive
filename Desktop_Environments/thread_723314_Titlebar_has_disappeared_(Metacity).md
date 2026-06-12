---
title: "Titlebar has disappeared (Metacity)"
date: 2008-03-13
forum: Desktop Environments
---

### Post by dcroxton on 2008-03-13
I was trying to do something in OpenOffice, but instead of the desired effect, I accidentally made OOo go full screen.  It's not the "view full screen" option in OOo, because I can go in and out of that, but the application still takes up the whole screen.  There is no titlebar and no window borders, and it covers up the Gnome panels, which any other app will not do.

I can get to the window menu by pressing alt+space, but the "move" and "resize" options are greyed out, as is "maximize."  I have tried selecting the "move titlebar onscreen" option, but it doesn't do anything.  All I can do is minimize and un-minimize the window.

There are many cases online of people losing their titlebar in compiz/beryl, but I'm not using those; just plain metacity.  It's probably not a bug, just some weird option that I typed by accident, but I have no idea how to get back the way it was.  Any help would be greatly appreciated.

Sincerely,
Derek

---

### Post by {BzF}~JOKesTER on 2008-03-13
Press F11

---

### Post by dcroxton on 2008-03-13
F11 opens the styles and formatting window in OOo.  I'm using an OOo that I installed from their website, because the Ubuntu one never works properly with extensions.

What are you expecting F11 to do?  It's not a "view full screen" issue with OOo, as I said.  I've tried the various shortcuts for Gnome -- Toggle fullscreen, Toggle maximization state, Unmaximize window -- but none of them do anything.  I've tried changing key bindings and making sure that they don't conflict with what's in OOo.  Still no help.

If there's some Gnome setting I can change by hand, I would be happy to do that.  Something is saving the window-less and titlebar-less state of the document I'm working on, because other documents do not open up like that.  I don't mind going into the xml files and tweaking a setting that I can't get to work with the gui, but I would need to have some idea of what I'm looking for.

If it's not Gnome at all, but OOo, that would also be a hint.  I don't think it is, because, as I said, this is not the "Full screen" view in OOo, and I don't know what other setting would cause the border and titlebar to disappear; but maybe there's something I don't know about.

Sincerely,
Derek

---

### Post by dcroxton on 2008-03-14
Anyone?

---

### Post by alberto ferreira on 2008-03-14
Probably the window got maximized and the titlebar is out of screen range. This happened to me before. Try closing that window, and open up another openoffice program like the presentation creator or whatever that is called, and change its sizen then close that window, and open up your problematic program.
If that doesn't work, try moving the mouse all way up in the screen and try to move the title bar. 

Hope it was useful

---

### Post by zach.detton on 2008-03-16
Try Ctrl+Shift+J. That's what OOo uses to toggle Fullscreen mode.

---

### Post by richiesgr on 2008-04-08
same issue nothing help

someone have another solution ?

---

### Post by dcroxton on 2008-04-08
I wish I could help, but my problem went away without any apparent cause.  I am using two monitors, and OOo instances on one monitor would open up correctly, but those on the other would appear without the title bar.  Moving a window from one monitor to the other would cause it to take on the behaviour of that monitor.  I gave up on it, then one day it just opened up properly again.

Sincerely,
Derek

---

### Post by wern0122 on 2008-05-29
I suddenly have this problem too, and I'm using the stock OOo that comes with Hardy.  The OOo method of getting out of fullscreen, shift-alt-j, doesn't fix the problem (it just toggles between two different fullscreen modes) and the F11 key doesn't do anything except bring up the styles window.  The problem persists if I turn on Compiz or turn off Compiz.  It's still fullscreen if I shut down the OOo program and open a new/different document. With any other program (terminal, gedit, etc), pressing the F11 key will fullscreen it or bring it back to having the titlebar. I guess you might consider this a bug with OpenOffice.org because it stole the F11 key and won't let the user interact with the windowmanager. Or you could consider it a Metacity & Compiz bug because window managers shouldn't be using such a simple hotkey as F11, which ought to be available to the running programs. It's frustrating, because the window is totally stuck.  :confused:

Anyone know how to either (a) turn off the hotkeys in OpenOffice? or (b) change the hotkey for fullscreen in Metacity? Either of these would fix the problem, and (b) is preferable I guess.

---

### Post by wern0122 on 2008-05-29
Changing the fullscreen hotkey for metacity doesn't work. I went to 

*System>Preferences>Keyboard Shortcuts*

and changed the "Toggle fullscreen mode" option to Ctrl-Alt-F, which still does nothing to fix my OOo window.

---

### Post by Mr Al on 2008-06-17
Same problem here.

---

### Post by AlexisCC on 2008-07-04
I too am having exactly the same problem with both Ubuntu distro and OOo distro.  Anything come of this?

---

### Post by BDNiner on 2008-07-05
This is also an issue for me, it happens when i have more than one open office window open at a time. normally moving the mouse over the area where the title bar is supposed to be brings it back and it doesn't happen when compiz is not enabled.

---

### Post by jamiedeith on 2008-07-11
This worked for me:

- Open a new OO session in the offending application.  (For me it was Writer.)
- Window/New Window
- Save the document to "Dummy" or something like that
- Exit OO
- Restart OO, it should be fixed.

Good luck!

Jamie

---

### Post by ellaguno on 2008-07-14
Same happend to me. I solved it resseting OpenOffice settings as explained in [this post]("http://ubuntuforums.org/showthread.php?t=441000&highlight=openoffice+fullscreen"):

Doing:

```
mv ~/.openoffice.org2 ~/.openoffice.org2_old
```

---

