---
title: "Notification area screw-ups"
date: 2010-09-09
forum: Desktop Environments
---

### Post by areeda on 2010-09-09
I get this problem fairly regularly.  it's on my laptop so it's gets rebooted every day.
What happens is that I get duplicates in the notification of the top panel that looks like:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=168917&stc=1&d=1284008300[/IMG]

One of the icons work normally the other doesn't it's dead area.  For example the only way to get to the wireless applet is that little corner sticking out behind the dead battery icon.

It would be cool if there is a way to get this to stop happening or lacking that how about a way to redraw the notification area with only working icons.

Thanks,
Joe

sorry if this posted, my search skills on this forum are not effective yet.

---

### Post by Gaygerbil on 2010-09-09
Your link is broken bro.

---

### Post by areeda on 2010-09-09
> **Gaygerbil said:**
> Your link is broken bro.
Thanks for the heads up.

Hopefully that is better.  It was viewing fine in my browser.  It's the full sized attachment.

---

### Post by kerry_s on 2010-09-09
i would remove them & re add them.
or
i would reset the panel by deleting ~/.gconf/apps/panel

---

### Post by areeda on 2010-09-09
> **kerry_s said:**
> i would remove them & re add them.
or
i would reset the panel by deleting ~/.gconf/apps/panel
Thanks for the tip Kerry.

It seems the only thing I can remove are the working ones.  I clicked on the left-most battery icon which is dead space evidently for everything except for "remove from panel" which removed the nm-applet which took me an hour to figure out how to get re-added.  Next time it happens I'll see if removing the "working" icon takes the extra one also.

So let me ask before I try the other suggestion.  I assume by delete you mean "rm -rf ~/.gconf/apps/panel"  there are a bunch of files and directories, how do I get them back (hopefully in the same configuration with all my custom launchers)?

Joe

---

### Post by kerry_s on 2010-09-09
> So let me ask before I try the other suggestion. I assume by delete you mean "rm -rf ~/.gconf/apps/panel" there are a bunch of files and directories, how do I get them back (hopefully in the same configuration with all my custom launchers)?


yeah, you can do it that way or in nautilus just press ctrl+h to show the hidden files.

after you remove it & log out & back in, it will be recreated, the panel will be stock, just like the first day you installed.

---

### Post by chriswyatt on 2010-09-09
I'm always getting notification bar glitches, definitely one of the weaker parts of GNOME.

---

### Post by areeda on 2010-09-09
> **kerry_s said:**
> yeah, you can do it that way or in nautilus just press ctrl+h to show the hidden files.

after you remove it & log out & back in, it will be recreated, the panel will be stock, just like the first day you installed.
OH.  A log out/log in fixes it anyway and leaves my other launchers intact.  That seems to be the best solution for now.

Thanks for the insight.

Joe

---

