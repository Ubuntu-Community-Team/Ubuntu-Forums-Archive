---
title: "Wrapping X to change the lServerLayout"
date: 2009-01-11
forum: Desktop Environments
---

### Post by Who on 2009-01-11
Hi,

On my HP 2133 I have to use the Via binary X drivers. In order to use an external monitor I need to change my server layout (i.e I define multiple server layouts in Xorg.conf, then start X with a different layout...)

Now, I wanted to do this in a nice, friendly way (like an icon on my panel - I don't mind having to restart X for it... but I do mind having to hand edit my gdm.conf-custom or my xorg.conf (either to specify the layout to use when starting X or to change the DefaultServerLayout). I don't want to have to type my root password to do this.

So, I wanted to do this:

mv /usr/X11R6/bin/X /usrX11R6/bin/X.real

Then create a new script for /usr/X11R6/bin/X (and chmod +x it...)
the script was
```

#/bin/bash
ACTIVE_LAYOUT=$(cat /etc/X11/activelayout)
exec /usr/X11R6/bin/X.real "$@" -layout $ACTIVE_LAYOUT
```

The file /etc/X11/activelayout can be written by me, and my panel icon echos out 'main' or 'randr' to specify the two different server layouts...

So, the idea is that it should behave just like normal X binary BUT it will add a serverlayout argument.

Now, I know that both of the layouts I'm specifying _work_ (if I specify them by editing gdm.conf-custom, it works) but the script as a whole doesn't... X won't start and I end up in the configuration X server.

Does anyone have any suggestions - I'm new to scripting, so it might just be something simple!

Thanks

Who

---

