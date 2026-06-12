---
title: "Cube server returns error..."
date: 2005-08-10
forum: Gaming &amp; Leisure
---

### Post by neilbain on 2005-08-10
Hi,

I suspect I am doing something really stupid here but....

I have successfully installed Cube on each machine on my home network (mix of Kubuntu and XP). Each runs single play mode with ease.  However, when trying to set the Kubuntu machine up as a server so that I can thrash the kids in a multi-player game, the 'linux_server' bin drops out with a "could not create server info socket" error.

Any thoughts on what to look for to solve this?

Thanks

Neil

---

### Post by wmcbrine on 2005-08-12
Start it as root? (sudo ...)

---

### Post by -Rick- on 2005-08-12
[QUOTE=neilbain]Hi,

I suspect I am doing something really stupid here but....

I have successfully installed Cube on each machine on my home network (mix of Kubuntu and XP). Each runs single play mode with ease.  However, when trying to set the Kubuntu machine up as a server so that I can thrash the kids in a multi-player game, the 'linux_server' bin drops out with a "could not create server info socket" error.

Any thoughts on what to look for to solve this?

Thanks

Neil[/QUOTE]
I only get that when the server port is already taken by some other app(like another cube process running).
Maybe you're running a client on the same machine with the -l (=listenserver) option?

---

