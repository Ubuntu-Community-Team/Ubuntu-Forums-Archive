---
title: "dead keys"
date: 2008-09-20
forum: Desktop Environments
---

### Post by marcthenarc on 2008-09-20
Having upgraded my Ubuntu to 8.04 from 7.10, I have had trouble getting my French Canadian keyboard back on track.  My dead keys don't work and the ca keymap does not have a nodeadkeys option I can disable (like some German keyboard maps). And all I get are `a `u ¨i instead of the accented keys - which I obviously cannot reproduce here. :-|

I've used EVERY old xorg.conf or XFree86.conf trick I could find or remember : ca_enhanced, ca(fr), all the KDE mappings.  I even read the source in /etc/X11/xkb/symbols/ca which seems to follow to the letter all the regular behavior of this particular keyboard.

I also thought that SCIM would be responsible, but after removing everything from that package and multiple reboots, it's a no go!  A small detail, though: I still have an $XMODIFIERS=@im=SCIM in my environment variables which I cannot get rid of, for the moment.

Any help appreciated.

-----------

Update:  I can use xterm without any accent problems.  What can possibly affect all other programs (KDE and non-KDE) but doesn't affect xterm ?

my current layout from .kde/share/config/kxkbrc is as follows:

```

[Layout]
DisplayNames=
EnableXkbOptions=false
IncludeGroups=
LayoutList=ca
Model=hp2501
Options=
ResetOldOptions=false
ShowFlag=false
ShowSingle=false
StickySwitching=false
StickySwitchingDepth=2
SwitchMode=Global
Use=true

```

Doesn't seems to have a lot to override, here.

Thanks again.

---

