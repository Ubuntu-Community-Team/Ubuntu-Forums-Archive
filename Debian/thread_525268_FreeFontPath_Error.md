---
title: "FreeFontPath Error"
date: 2007-08-14
forum: Debian
---

### Post by amrclutch1 on 2007-08-14
While tinkering with /etc/X11/xinit/xinitrc I came across this error while trying to run "startx".

```

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

```

Here is the xinitrc

```

#!/bin/sh
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script

. /etc/X11/Xsession &
xsetroot -solid "#346679"

```

The above crashes to the error message I posted, this doesn't.

```

#!/bin/sh
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script

. /etc/X11/Xsession

```

I just figured out that the error message is echoed no matter what, but why is X crashing with my edited version?

---

### Post by amrclutch1 on 2007-08-14
Please reply! :(

---

