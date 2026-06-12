---
title: "Title Bar Bug (Visual Effects)"
date: 2009-02-20
forum: Desktop Environments
---

### Post by Johnny W. on 2009-02-20
So, hey, I'm new to the forums, and I'm only asking this, because I can't *seem* to find the answer anywhere... I don't know if I'm phrasing the question wrong, or what, but:

[IMG]http://i498.photobucket.com/albums/rr344/JohnnyWuzzisname/errorReport.jpg[/IMG]

When I enable the advanced/normal Visual Effects in Intrepid, this is what happens when I mouse over the exit button. It's a small little bug, and I've tried disabling vast combinations of features using Compiz...

Just to help you out, I'm running Intrepid on an HP dv2500, on the NVidia 177 driver, with Compiz installed, Emerald not, and I doubt Beryl... Nope, no Beryl, I just checked to make sure.

Any help would be appreciated, and I'd really hate to sound redundant if this has been asked before.

---

### Post by IceReaver75 on 2009-02-20
its a well known nvidia bug.  There are 3 options really 

1) just dont use the compiz effects

2) try using a different theme than the human theme.   Clearlooks seems to not have that problem

3) do what i had done and just manually install the 180.29 drivers from the nvidia site.  That solved all problems.  Only problem with going that route is you have to re-install the drivers with any kernel update.

hope that helps some

---

### Post by Johnny W. on 2009-02-20
Well, I tried changing themes, I'm in Darkroom right now, and it's still popping in and out. 

As for installing the NVidia 180.92 driver, I did, but to no avail, the computer didn't even boot with graphic display, so I junked that driver...

I guess the only thing left to do is give up the dreams of having Gelatin-enabled windows... What has this world come to?! Noez!

---

### Post by Johnny W. on 2009-02-20
Oh, looks like I've done it. You were totally right. Despite being within the Darkroom theme, it still used the Clearlooks title bar, so of course, I kept getting the error.

To fix the problem, you'll want to go to System -> Preferences -> Appearance, then choose the theme you're likin', and click on Customize. Once in here, click on the 'menu bar' tab and choose whatever suits your fancy, that isn't 'Human' or 'Darkroom'. These are the two that I noticed the problem with, but the Clearlooks menu bar seems to work just fine.

---

### Post by keithwwalker on 2009-02-22
I have been recently frustrated with this as well.

Here are some of the threads that I have looked at that haven't solved the issue:

[http://ubuntuforums.org/showthread.php?t=574368&highlight=title+bar&page=2]("http://ubuntuforums.org/showthread.php?t=574368&highlight=title+bar&page=2")

[http://ubuntuforums.org/showthread.php?t=599010]("http://ubuntuforums.org/showthread.php?t=599010")

[http://ubuntuforums.org/showthread.php?t=709330]("http://ubuntuforums.org/showthread.php?t=709330")

[http://ubuntuforums.org/showthread.php?t=652286]("http://ubuntuforums.org/showthread.php?t=652286")

What I did to restore the title bar minimize, maximize and close buttons is to system>appearance>visual effects , and then noticed of the three options (none, normal, extra) that none of these were enabled, even though I was running compiz visual effects.

I clicked on extra, and that restored the title bars.

You may have to go back to the compiz control panel to re-enable some features...

I just wonder if the problem starts with compiz 'opacity, brightness, saturation' settings?

~~~~~~~~~~~
I also had a separate problem with window title bars overlapping the control panel.  A toggle of compiz's workaround for Firefox fixed that.

---

