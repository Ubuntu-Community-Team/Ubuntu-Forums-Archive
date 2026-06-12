---
title: "dialogs inaccessible off screen"
date: 2007-06-29
forum: Dell  Ubuntu Support
---

### Post by kenbaldwin on 2007-06-29
I got my Dell E1505N with Wide Screen XGA screen a few days ago.

Sometimes I get app dialogs that extend below the bottom of the screen, and I can't figure out how to access the part that's hidden. There doesn't seem to be any way to drag the dialog higher, because I can't drag it above the top of the screen. For example, the Preferences dialog in gtkpod extends so far down that I can't see (or select) the Cancel/OK buttons, and therefore can't set any preferences.

I installed the 915resolution package, because several reviews said it was necessary, but now I'm wondering if that was a mistake. My screen resolution (System | Preferences | Screen Resolution) is currently set to 1280 x 800, which seems correct. Does the system think my screen in larger than it really is, or is there some trick I'm missing? Thanks

Ken

---

### Post by neptho on 2007-06-30
Have you tried clicking the 'maximize' button at the top of the dialog?  If it's disabled, there's usually a way, such as a button on the top left, which enables you to choose minimize, maximize, et al.

---

### Post by kenbaldwin on 2007-06-30
Thanks, but no change. The dialog already extends from the very top of the screen to below the bottom. Maximizing changes the icon, but the dialog moves only slightly. It really seems like the system thinks my screen is taller than it is...

---

### Post by kenbaldwin on 2007-06-30
Just to be sure, I tried removing 915resolution and restarting, but that didn't help. Just made me screen fuzzy and stretched.

---

### Post by neptho on 2007-06-30
Do you have your virtual resolution set higher than the screen?

```
%xdpyinfo | grep dimensions
```

That should tell you what size the screen *thinks* it is.  If it's too large:

```
%sudo sudo dpkg-reconfigure -phigh xserver-xorg
```

to reconfigure your X server's settings.  Pay attention to the name of the backup it makes in case if you need to copy it back into place.

---

### Post by kenbaldwin on 2007-06-30
Thanks, but that also reports 1280x800 pixels (332x212 millimeters).

Ken

---

### Post by jplowman on 2007-08-31
I am experiencing the same problem. I have a Toshiba Libretto L5 with 1280x600 screen resolution. The Print dialog in Adobe Acrobat Reader extends below the bottom of the screen and I don't know how to make it all visible.

It's annoying because I'm having toruble getting Acrobat to print to a PDF file... it's working in Abiword, but for some reason Acroread isn't doing it properly. I have a feeling the answer may be in that bit of the dialog box that's out of sight...

There must be some way to get a look at it, no?

---

### Post by kuja on 2007-08-31
To move those oversized/out-of-screen windows you can probably just alt+click & drag.

---

### Post by jplowman on 2007-08-31
Thanks kuja - alt+click and drag does work to move the dialog box up. Alt+F11 is another way, it makes the dialog box fullscreen and doesn't let any of it extend past the screen edges.

Acrobat reader still isn't putting the pdf file in my home folder's PDF folder when I print though. No idea why. Sigh...

---

