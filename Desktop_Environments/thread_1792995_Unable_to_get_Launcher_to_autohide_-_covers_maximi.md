---
title: "Unable to get Launcher to autohide - covers maximised windows"
date: 2011-06-28
forum: Desktop Environments
---

### Post by rover_and_out on 2011-06-28
I just got round to upgrading to 11.04 over the weekend, and generally I'm happy with the new desktop - except...

In common with several others I appear to be unable to get the launcher to autohide, except this is not a sudden occurence - it has never autohidden, even immediately after install.

Steps tried include:

1. Log Out / In and reboot
2. Installing Compiz Config Settings Manager - I have tried all the options for autohide, with no change
3. Setting the autohide to none - with a widescreen laptop this wouldn't have been disastrous, but maximised windows still fit behind the launcher.
4. Dragging icons from the desktop to the launcher on various workspaces - still no effect.

I don't want to have to resort to Ubuntu Classic, but not being able to use maximised windows is a bit of a pain.

Any further suggestions?

---

### Post by steinerd on 2011-06-28
First try the link to this tool, [http://shallows.bounceme.net/tiki-index.php?page_ref_id=20](http://shallows.bounceme.net/tiki-index.php?page_ref_id=20) thinking it won't change much but makes it easier than fishing through CCSM.  Next the only thing I can think of that might interrupt the autohide feature on a new install is possible the autohide animation.  Try changing those settings if you have not already.  Also I would make sure that you don't have any other edge triggers set, at least to start with.  I would make sure that the default settings are in place by typing...

```
<ALT> <F2>
unity --reset
```

Explained here [http://shallows.bounceme.net/tiki-index.php?page=Reset+Unity+Desktop+and+Icons&structure=Ubuntu+Help&page_ref_id=21](http://shallows.bounceme.net/tiki-index.php?page=Reset+Unity+Desktop+and+Icons&structure=Ubuntu+Help&page_ref_id=21) Then use the linked tweak tool to set-up your autohide options.

Hope this helps...

---

