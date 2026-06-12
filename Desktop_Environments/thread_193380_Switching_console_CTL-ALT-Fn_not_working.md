---
title: "Switching console CTL-ALT-Fn not working"
date: 2006-06-09
forum: Desktop Environments
---

### Post by hoodwink on 2006-06-09
On any other distro, I can use CTL-ALT-Fn to switch away from the gui console (usually 7), login, issue commands, and logout.

On Kdapper, when I do this, the console is garbled and does not recognize line feeds. When I get a login prompt and enter a user id, the password prompt appears on the same line, and it's impossible to enter a password.

Any idea how to fix this?

---

### Post by hoodwink on 2006-06-10
[QUOTE=hoodwink]On any other distro, I can use CTL-ALT-Fn to switch away from the gui console (usually 7), login, issue commands, and logout.

On Kdapper, when I do this, the console is garbled and does not recognize line feeds. When I get a login prompt and enter a user id, the password prompt appears on the same line, and it's impossible to enter a password.

Any idea how to fix this?[/QUOTE]
OK, folks, this is super weird. If I switch to tty1, 5, or 6, the console operates normally (I can login), but if I switch to tty2-4 the console is garbled as described before.

---

### Post by hoodwink on 2006-06-18
[QUOTE=hoodwink]OK, folks, this is super weird. If I switch to tty1, 5, or 6, the console operates normally (I can login), but if I switch to tty2-4 the console is garbled as described before.[/QUOTE]
Just an update for anyone else. My box has an onboard SIS card, and it appears that the current kernel (?) and/or X driver for sis (?) has screwed the pooch. Still works fine on an older kernel/sorg release (CentOS 4.3). SIS is known to be a troublesome beast, but it's always worked until now.

---

