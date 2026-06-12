---
title: "Replacing xfdesktop in 16.04"
date: 2017-08-05
forum: Desktop Environments
---

### Post by arsenic23 on 2017-08-05
I stuck with 12.04 way longer then I needed to.  It was very comfortable and I had invested an obscene amount of hours in customizing it.  I've just put together a new main system, so I've went ahead and transitioned to 16.04 (xfce).  Getting it set back up the way I like has been way easier then the last time, but I still have one sticking point preventing my complete happiness.  I can't seem to replace xfdesktop.

I hate xfdesktop.  I dislike the boxes surrounding the filenames, and I dislike the fact that I can't pile my files up in untidy bunches.

What I've done in the past is kill and disable xfdesktop, and then load nautilus with xfce's session manager.  It would then take control of rendering the desktop.  This no longer works.  Not that I want modern nautilus anyway: there is no way I'm having zeitgeist on my system.  So my plan was to do the same as I always have, but instead use mate's nautilus fork caja.  This fails as well.   In fact I can't seem to get anything to render the desktop for xfce in 16.04.  It just lives there, a black emptiness.  Only xfdesktop will work.

Now I'm not attached to any particular desktop renderer; I just want something that will replace xfdesktop in the newer xfce, let me pile my files on top of one another, and hopefully look a little better.

I've tried everything I can think of, including using dconf-editor and mate-control-center to make sure caja is set to render icons and wallpaper on the desktop.   I could really use some thoughts and suggestions.

---

### Post by &amp;KyT$0P# on 2017-08-05
In [FONT=Courier New]~/.cache/sessions[/FONT], there should be a file named like
```
xfce4-session-<hostname>:<display number>
```
I was able to get PCManFM as desktop manager by editing this file manually, replacing the xfdesktop commands with PCManFM commands.

Not sure how good a solution this is, as the splash screen hangs for a while on "Starting pcmanfm", after PCManFM was started.  And PCManFM never showed up in the XFCE session manager at all. :confused:

So I recommend you **back up your system before trying this**.

---

### Post by arsenic23 on 2017-08-05
Upon looking at my sessions file I discovered that xfdesktop was still listed there even though it didn't appear to be loading and I had removed it from the session with the gui tool.
After removing it caja did take control of the desktop, once.   After logging out and logging back in I could not replicate my success.  After a good bit of trial and error I again got it to render the desktop by constantly mashing 'killall xfdesktop && caja -n' into a terminal.  This also was a fluke I could not replicate.   So, this should work, but it mostly doesn't.

In order to find out what was causing this I tried several different things.  I killed all non-essential running processes with not luck.  I reset many settings and files and started the process of trail and error from the beginning.  Then I installed (temporarily) a few other file managers.

pcmanfm takes over the desktop perfectly;  I have no intention of using it.
nautilus takes over the desktop perfectly; I'd use it if ziegiest wasn't a dependency and it didn't cause issues with setting and keeping a desktop background.  ( That's probably a fixable problem, but I dislike modern nautilus enough to not want it on my system.
nemo also took control of the desktop with no problem.  Currently, it is what I'm using.

At this point it looks like there is some problem with caja itself and not how I was trying to set it up in xfce.

I would honestly stop here and call it "fixed", but I have one big related problem.  I can't copy and paste files between any file managers.  I've always used multiple file managers and I don't remember this ever being an issue in the past.  This means, if nemo is putting the icons on my desktop I can't copy and paste files between the desktop and whatever file manager I'm using, in this case caja.

I'd consider switching to mate, but I rather do love everything about xfce that isn't Thunar and xdesktop.


EDIT 20170809:
I'm now using nautilus instead of nemo.  Fixing a bug that caused compiz to break alt+f4 every login caused the desktop image to stop working in nemo.  Updating nemo fixes this, but the stand alone nemo depends on zeitgeist.  So, might as well just use nautilus.  I believe I've disabled zeitgeist's functionality with some file system hacks.  I really wish I could ditch compiz, but I can't seem to get all of my shortcuts working in any other window manager.

---

