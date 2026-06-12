---
title: "can't start desktop if user wasn't properly logged off - 10.04"
date: 2010-07-14
forum: Desktop Environments
---

### Post by spamhog on 2010-07-14
10.04, clean installs, running Gnome or LXDE.

IF
- a logged-on user wasn't properly logged off
- the system is restarted
- the same user attempts to log in
THEN
- only the wallpaper and the arrow cursor appear
- the user is logged in but can't log off the semidead GUI
- it's necessary to drop to CLI and restart the desktop
- that user remains borked as far as X is concerned
- another user is needed to do any work in X

This seems repeatable, and happened on 2 different PCs.

When logged into Gnome as another user and trying to sudo a backup of the borked user's home before attempting a repair, a ".gvfs" file is reported "in use" and can't be copied.

It happened to me quite a few times, due to crash or more often power failure, or my sudo-errors.  I now keep a few spare virgin sudo-enabled cloned accounts just in case one dies that way.

I bet the proper fix is simple, but I can't find this problem in the knowledge bases.  Ideas?

---

### Post by pastalavista on 2010-07-14
You can reset that user's desktop settings to default (and then modify all over, unfortunately) by deleting the gnome configuration folders (hidden) in that user's home directory (.config, .gconf .gconfd) or any others you might have modifed recently. Change will take effect after logout/login.

---

### Post by spamhog on 2010-07-15
Thank you pastalavista!  The only thing that seems to trigger this behavior is an attempt ro start a user's desktop without a previous orderly logoff.  If the user isn't logged on, it's not affected.
[LIST]
[*]When the user is logged on, do .config, .gconf .gconfd change to, and stay in, a state incompatible with starting the desktop?
[*]If so, do you know if they undergo a text content change or is it only a filesystem flag?
[/LIST]

---

### Post by Unhackmee on 2010-07-17
The power cord came off my netbook and this happened. Although in my case, after i login, a black screen appears with some text and instantaneously disappears. So far, i havent been successful in reading the message.

So does this mean i have to make a new user and configure everything to my liking all over again? for example, having to setup IM accounts. or can i just login via terminal and copy the whole user directory and just overwrite the new user's home with it and would my application preferences be saved? what should i NOT copy?

sorry if its a little too many questions. 

PS: 'gnome', 'failsafe gnome', 'ubuntu netbook edition', 'ubuntu netbook edition 2D', 'xterm'  ....... all these yield the same result.

---

