---
title: "help uninstalling planeshift"
date: 2007-09-29
forum: Gaming &amp; Leisure
---

### Post by nofx135 on 2007-09-29
i installed planeshift and i now want to uninstall it but i cant through either synaptic or add/remove programs. i tried using the PlaneShift uninstaller which was under my games menu but it gave me this error:

Could not launch menu item
Failed to execute child process "/opt/PlaneShift/uninstall" (Permission denied)

can anybody tell me other ways of uninstalling this game?

---

### Post by nofx135 on 2007-09-29
got it
i just cd to opt/ planeshift and ran the uninstall as root

---

### Post by Scott O'Nanski on 2009-01-07
I'm having the same issues, can you please document for others how you accomplished this?

Please be specific.

Thanks.

---

### Post by bubwitmaingay on 2009-07-09
I successfully removed PlaneShift

1. Open the terminal
2. type: "su" (that is without the quotes)
3. enter your password for root
4. type: "cd ..", until it reaches the root folder
5. type: "cd /opt/PlaneShift/"
6. type: "./uninstall"

...and a window will appear asking you to uninstall the game. The reason why I haven't opened the folder is that I thought the folder name is "planeshift", and it was actually "PlaneShift".

Hope that helps. 8)

---

### Post by bubwitmaingay on 2009-07-09
To access the game, you should install it SYSTEM-WIDE and you should allow permissions, create a users and group name. I was able to play the game using the administrator account (that's my login). 8)

---

