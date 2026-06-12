---
title: "windows with oversized geometry"
date: 2009-09-05
forum: Desktop Environments
---

### Post by tty on 2009-09-05
Under GNOME, I am trying to create a window that is larger than the visible screen.  I would
like that the window goes slightly off the borders.  To get that effect I do:

1 Click the two panels together (by first enabling the property "Show hide buttons).

2 The program to start up, has the nodecoration hint set.  This is recognized by GNOME,
as the window does not show a title bar any longer.

3 The geometry of the program is +-12+-2  So the window should be shifted 12 pixels
to the left off the window and 2 pixels upwards. Further, the size of the window makes
the right and bottom border to be off the screen.

4 The geometry is "reapplied" several times.  In earlier versions of GNOME and KDE,
this was necessary to insist on the particular geometry.  So while those windowmangers
resized the geometry a couple of times, they gave up eventually.  Current GNOME versions
seem to ignore this completely.

While step 1 and 2 work, step 3 and 4 seems to be ignored by GNOME: The window is
always put back into the visible area.  The only way so far under Ubuntu to get the desired geometry
is under a failsafe session (aka xterm).

(I am using the latest development version of Ubuntu, but I am aware that this problem exists
already for years.  It's only now that I consider to switch to Ubuntu myself)

---

### Post by jpeddicord on 2009-09-05
Why not just set the window to be fullscreen? That will cover panels and other sticky widgets.

If you're talking about this in terms of programming:

> gdk_window_fullscreen ()

void                gdk_window_fullscreen               (GdkWindow *window);
Moves the window into fullscreen mode. This means the window covers the entire screen and is above any panels or task bars.

If the window was already fullscreen, then this function does nothing.

On X11, asks the window manager to put window in a fullscreen state, if the window manager supports this operation. Not all window managers support this, and some deliberately ignore it or don't have a concept of "fullscreen"; so you can't rely on the fullscreenification actually happening. But it will happen with most standard window managers, and GDK makes a best effort to get it to happen.

window*: a toplevel GdkWindow
Since 2.2

---

### Post by tty on 2009-09-05
> **jacobmp92 said:**
> Why not just set the window to be fullscreen? That will cover panels and other sticky widgets.

I succeeded to make panels ago away, by clicking them together (step 1).  They still remain as a tiny
box in a corner, but that is fine with me.

What I want is a window, that is slightly larger such that I can fit exactly the content into the visible part.
Do you believe that your suggestion might solve this problem as well?

Ideally I could just set with xprop the property in question.

---

### Post by jpeddicord on 2009-09-05
> **tty said:**
> I succeeded to make panels ago away, by clicking them together (step 1).  They still remain as a tiny
box in a corner, but that is fine with me.

What I want is a window, that is slightly larger such that I can fit exactly the content into the visible part.
Do you believe that your suggestion might solve this problem as well?

Ideally I could just set with xprop the property in question.

If you make it fullscreen, yes, the window will be on the entire screen, which includes covering up the panels.

---

### Post by tty on 2009-09-05
But can it be larger?

The program in question (emacs btw), runs on a quite old server (2.2.14 Kernel with Redhat 6.2).

---

### Post by jpeddicord on 2009-09-05
> **tty said:**
> But can it be larger?

The program in question (emacs btw), runs on a quite old server (2.2.14 Kernel with Redhat 6.2).

Why would you want to make emacs larger than the screen? If you want to hide the UI completely, you may want to just check out some emacs options for doing so. If you want a full terminal environment, just hit Ctrl-Alt-F1 to switch to a VT and Alt-F7 to switch back to X.

---

### Post by tty on 2009-09-05
> **jacobmp92 said:**
> Why would you want to make emacs larger than the screen? If you want to hide the UI completely, you may want to just check out some emacs options for doing so. If you want a full terminal environment, just hit Ctrl-Alt-F1 to switch to a VT and Alt-F7 to switch back to X.

I have no choice on this side.  Emacs runs under X combined with some graphics on a quite old server. And all depends on respecting X geometry specifications.  Otherwise windows are badly arranged.

The alternative would be to recommend a failsafe session for Ubuntu only.

In this case, most people will prefer to switch to Cygwin.

So if I correctly understand you, there is no way that GNOME interprets a geometry specification completely.

---

### Post by tty on 2009-09-06
In the meantime I tried xnest.  But it has exactly the same problem.  GNOME insists on decorating the root window with a title bar.  Someone asked a related question some time ago but did not receive  any reply.
[http://ubuntuforums.org/showthread.php?t=262607](http://ubuntuforums.org/showthread.php?t=262607) 

And I installed also kubuntu - but KDE seems to insist on geometries in the same manner.  In earlier versions (KDE 2.2.1) it was still possible to get the desired geometries.

---

### Post by jpkotta on 2009-09-07
> **tty said:**
> I have no choice on this side.  Emacs runs under X combined with some graphics on a quite old server. And all depends on respecting X geometry specifications.  Otherwise windows are badly arranged.

The alternative would be to recommend a failsafe session for Ubuntu only.

In this case, most people will prefer to switch to Cygwin.

So if I correctly understand you, there is no way that GNOME interprets a geometry specification completely.

If you're talking about the command line -geometry switch, then Gnome or any other WM doesn't interpret it, it's the application.

Are you running Emacs on the remote machine and using a local X server?  Or are you doing some sort of VNC type thing where both Emacs and the X server are remote?

---

### Post by tty on 2009-09-08
> **jpkotta said:**
> If you're talking about the command line -geometry switch, then Gnome or any other WM doesn't interpret it, it's the application.

Are you running Emacs on the remote machine and using a local X server?  Or are you doing some sort of VNC type thing where both Emacs and the X server are remote?

Emacs runs on a remote machine. That machine is a (very old - see above) server (in the usual sense), but certainly not the X-server (which is in  X terminology where the screen is). The X server is on the user's side a (relatively) newly installed machine with (e.g.)  Gnome (or another environment). So the user types in his Gnome-environment  ssh -X remotemachine to get several windows: one from Emacs and one from other windows (actually ghostview)  which also depend on exact geometry interpretation.

The geometry switch -geometry is indeed interpreted by the application (here, emacs).  But that application always attempts to get the new place (with negative coordinates), unfortunately Gnome does not tolerate that.  Earlier Gnomes (long ago) attempted to reposition the window for a couple of times and then gave up. The new Gnome is stricter.

What indicates that this is not an inherent problem of Gnome is that I can manually move the window (with Alt-Mouse1) to the desired negative geometry position by first moving it much farther away to get over the "resistance" of the border and then back.  So why should a program be able to do the same?

In the long term it might be possible to replace emacs with a newer version (23 is much better in that respect).  But currently (next years) that is no option.

---

### Post by jpkotta on 2009-09-09
> **tty said:**
> Emacs runs on a remote machine. That machine is a (very old - see above) server (in the usual sense), but certainly not the X-server (which is in  X terminology where the screen is). The X server is on the user's side a (relatively) newly installed machine with (e.g.)  Gnome (or another environment). So the user types in his Gnome-environment  ssh -X remotemachine to get several windows: one from Emacs and one from other windows (actually ghostview)  which also depend on exact geometry interpretation.

The geometry switch -geometry is indeed interpreted by the application (here, emacs).  But that application always attempts to get the new place (with negative coordinates), unfortunately Gnome does not tolerate that.  Earlier Gnomes (long ago) attempted to reposition the window for a couple of times and then gave up. The new Gnome is stricter.

What indicates that this is not an inherent problem of Gnome is that I can manually move the window (with Alt-Mouse1) to the desired negative geometry position by first moving it much farther away to get over the "resistance" of the border and then back.  So why should a program be able to do the same?

In the long term it might be possible to replace emacs with a newer version (23 is much better in that respect).  But currently (next years) that is no option.

Most X applications allow you to specify both an origin and an offset in their geometry spec.  Apparently Emacs doesn't:
> 
 -- Function: set-frame-position frame left top
     This function sets the position of the top left corner of FRAME to
     LEFT and TOP.  These arguments are measured in pixels, and
     normally count from the top left corner of the screen.

     Negative parameter values position the bottom edge of the window
     up from the bottom edge of the screen, or the right window edge to
     the left of the right edge of the screen.  It would probably be
     better if the values were always counted from the left and top, so
     that negative arguments would position the frame partly off the
     top or left edge of the screen, but it seems inadvisable to change
     that now.


However, I would be extremely surprised if you couldn't do this in some other way.  For example, in my window manager (fvwm) I can move a window like so:
```
Move +-100p +-100p
```
which means move the top left corner 100 pixels above and to the left of the top left screen corner.  There used to be a package called devil's pie that did all sorts of custom window management for Gnome, maybe try that.  

The window manager always has ultimate control on the placement of windows, all the application can do is try to hint and override it.

---

### Post by tty on 2009-09-09
> **jpkotta said:**
> Most X applications allow you to specify both an origin and an offset in their geometry spec.  Apparently Emacs doesn't: ...

There were some misunderstandings of geometry specs in Emacs some time ago.  Code got written with it and now nobody dares to correct that. This does it:
```

(modify-frame-parameters ()
      '((user-position . t)
        (top - 0)
        (left + -4)))
```C-x C-e it! As long as the value is positive the window is pushed around as expected, but with negative integers the request is ignored.

Here is my current solution:
```

killall -9 compiz.real
ssh -X host
```When the screen is opened move with Alt-Mouse1 the window over the left border. Then reapply the originally intended geometry (fortunately it's already bound to a key...). It seems that a window that has already "illegal" geometries has now the liberty to determine its own fate.  Would be nice if there would be a more strait forward solution though... It doesn't look very nice to have such instructions for Gnome, compared to the cygwin solution that just works out-of-the-box.

Other Windowmanagers like fvwm work.

Thanks for the hint for devilspie.  I installed it - but this requires even more complex user interaction: Installing the tool etc.

---

### Post by tty on 2009-09-09
I finally went through the Extended Window Manager Hints that Gnome/Metacity probably implements.

[http://standards.freedesktop.org/wm-spec/wm-spec-latest.html](http://standards.freedesktop.org/wm-spec/wm-spec-latest.html)

It seems there is no clean way to specify what I want. That's not too surprising as new apps should indeed be more collaborative than just taking the entire screen + using unusual geometries. There seems to be no hint about the size of a window. There _NET_WM_FULL_PLACEMENT, but even that does not sound very convincing.

The problem with  devilspie is that it is on the screen side.  For each resolution a new entry would be needed. It is not simple to keep this up-to-date.  What would be ideal is just a hint saying: Take the geometries literally.

---

### Post by tty on 2009-09-10
Another attempt: Thanks to this howto I got Xephyr running. > **bodhi.zazen said:**
> How to Xephyr
Unfortunately all special keys are unknown (cursors, page up/down, menu).
```

Xephyr -ac -fullscreen -reset -terminate :1 & sleep 2 && env DISPLAY=:1.0 xterm

```
Another disadvantage here is that Emacs cannot check any longer for visibility. This is performed by moving the mouse into some place and then checking if it is at that place (set-mouse-position and mouse-pixel-position). This is quite important in Emacs: The echo area (bottom line) must not be hidden by a panel. Beginners have quite some problems with that...

---

