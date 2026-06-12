---
title: "nxclient and problems with 12.04 (screen resolution)"
date: 2012-10-02
forum: Desktop Environments
---

### Post by jbeiter on 2012-10-02
My client system running nxclient is ubuntu 12.04, the host I am connecting to is running 11.04 (nxserver)

before upgrading to 12.04, I experienced problems with the remote screen displaying just the upper-left 80% (so the bottom panel w/menus was not visible) but if I disconnected and re-attached, it would usually render ok.

When I upgraded my home pc to 12.04, it will not automatically adjust at all. I can get the bottom panel visible by playing with xrendr but it's still not rendering right and won't resize to the whole screen.

Does anyone know of a work around for this?

I'm using stock gnome for 11.04 on the nxserver machine, I've tried ubuntu/2d, gnome under cinnnamon, and cinnamon on the nxclient machine with no help.

---

### Post by jbeiter on 2012-10-11
no suggestions at all? I'm the only person in the universe to experience this?

Please someone throw me a bone to try. This is killing me.

---

### Post by cjhabs on 2012-10-11
I changed the resolution on the server display to    	 	 	 	 	1680x1050 to work correctly with the NX client - that did the trick for me.

---

