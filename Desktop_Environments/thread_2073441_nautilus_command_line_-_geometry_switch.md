---
title: "nautilus command line - geometry switch"
date: 2012-10-19
forum: Desktop Environments
---

### Post by foberle on 2012-10-19
Using Ubuntu 12.04
When creating launchers or using the command line, e.g. "nautilus folder-name," I've attempted to use the --geometry= option, but it seems to have no effect whatsoever.

No other instances of nautilus are running when I attempt this. Also, on various web sites, I have found the parameters to be specified as:

--geometry=widthxheight+horizontal_location+vertical_location (all in pixels I presume)

and it seems that the horizontal and vertical locations are optional.

From the man page, it looked like I might need to add the "--no-desktop" option as well to override the settings from the nautilus preferences, although I found nothing in preferences related to window positioning. In any case, this made no difference either.

I should mention that I have a "fixed window" setting for nautilus in the Compiz-Config-Settings Manager. Does that override even the command line options?

Thanks for any help.

---

### Post by maphilli14 on 2012-10-22
I too see this issue.  It doesn't appear to be related to Compiz, as if i switch to metacity the issues still appears.

---

