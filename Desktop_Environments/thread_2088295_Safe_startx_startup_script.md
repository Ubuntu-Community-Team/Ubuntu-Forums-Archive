---
title: "Safe startx startup script"
date: 2012-11-26
forum: Desktop Environments
---

### Post by st0ne2thedge on 2012-11-26
Hi, after deleting my DM i started to look for a safe way to start my X environment after logging in from console.
```

#!/bin/bash
# VincyDE
# -------
# Vincent Van Driessche

# Hier zorgen we ervoor dat de control + Z combinatie er niet voor zorgt
# dat iemand commandos kan uitvoeren in mijn systeem.

# Een handig commando voor trapping is 'trap -l' dit geeft een lijst van
# alle traps op je systeem.
echo "starting"

trap "you failed!" TSTP;
startx;
exit;

```
As you'll see in the above bash code, i'm trapping the <ctrl>+Z combination and eventually exiting when the x server is shutdown. Doing so my user is logged out when someone manages to stop my X. The problem is when someone stops the bash process, they can still return to the runlevel i started the script in and then issue commands onder my user. Does anyone have a sollution to this?

The "u failed!" message is also never displayed.

---

