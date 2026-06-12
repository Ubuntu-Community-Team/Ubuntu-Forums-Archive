---
title: "Screen Resolution problem AFTER dual screen attempt aborted"
date: 2009-12-23
forum: Desktop Environments
---

### Post by ptaljaard on 2009-12-23
Hi There.

I am running Ubuntu 8.10.
My Ubuntu skills are about 5/10.

I found an old monitor that I thought would be nice to connect to my HP Laptop. I would find a dual-screen set-up helpful for my work.

Anyway, I connected the old monitor and went to System/Preferences/Screen Resolution. Once there, I unclicked the "mirror" option and "activated" the second monitor.

After I clicked "apply" I got the following message:

"Monitor Resolution Settings has detected that the virtual resolution must be set in your configuration file in order to apply your settings. Would you like Screen Resolution to set the virtual resolution for you? (Recommended)".

I followed the recommended procedure.

I logged off and when I logged in the dual screens worked fine, except for the fact that the laptop screen resolution was less clear than before. I thought nothing of it.

After playing with the dual screen for a few minutes I decided to go back to my original, single-screen, setup.

THIS IS WHERE THE PROBLEM STARTS.

I am now unable to change my laptop screen resolution back to what it was before. The are now only 3 options available to me, the best being 1024 x 768. I am really unhappy and would like to have my screen resolution higher, as it was before.

I have no idea what to do. I have searched around but couldn't find a solution.

Please could someone be kind enough to help me.

Thank you in advance.
Pierre

---

### Post by quixote on 2009-12-24
I had no end of trouble trying to echo the output of a laptop screen to a video monitor.  That's a different problem than yours, but maybe what finally worked for me will help you.

The gui tools don't seem to work most of the time.  I found I could get what I needed by using command line "xrandr".  For instance, output to second monitor:
```
$xrandr --output VGA --mode 1024x768  *[or whatever the 2nd screen resolution is]*
```

There's a [page on xrandr]("https://wiki.ubuntu.com/X/Config/Resolution") with instructions on how to try all sorts of different resolutions.  It's a bit tedious at first, but the nice thing is, it really does work after you slog through it all.  It also has instructions on how to change resolutions in /etc/X11/xorg.conf, which may be another thing worth looking at in your case.  Possibly a change in resolution was written to that file by the gui, but it didn't "unwrite" it when you wanted to revert.

---

