---
title: "All screensaver have vanished!"
date: 2007-09-07
forum: Desktop Effects &amp; Customization
---

### Post by ephonk on 2007-09-07
Using Kubuntu Feisty with no Compiz, no Beryl, no whizzy effects...

Somehow my screensaver configuration utility has gone completely blank.  No screensavers are listed.  I know they still exist, it comes up at the anticipated timeout.  I can run glxgears from the console and it pops up in a window, but it doesn't show in the screen saver settings.

I've uninstalled and reinstalled kscreensaver in adept and it has made no difference.

Don't know how long this might have been this way - I only noticed it now because I was trying to install Electric Sheep (I can run THAT from the console too).

So how does the settings utility know what screen savers are installed?

thx...

---

### Post by ephonk on 2007-09-08
Update...

I thought, "What is the screensaver control app looking for?" so I went looking.  Supposedly, it's looking for .desktop files.  I found some docs that say you can disable screensavers by renaming its .desktop file to something else.

So I found 24 .desktop files in /usr/share/applnk/System/ScreenSavers.  Right where they were supposed to be.  Got all the referenced .kss files in /usr/bin as well.

So I still don't see what the problem is.  I just have more info.

What tells the config app where to locate the .desktop files?

---

### Post by ephonk on 2007-09-15
Still doesn't work.  Still don't know why.  I can run all of them from the command line.  I can even change the screen saver by editing the appropriate file.  I just want to see the GUI applet work.

---

