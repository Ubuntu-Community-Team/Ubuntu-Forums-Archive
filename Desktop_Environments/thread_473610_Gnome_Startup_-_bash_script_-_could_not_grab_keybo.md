---
title: "Gnome Startup - bash script - could not grab keyboard."
date: 2007-06-14
forum: Desktop Environments
---

### Post by MattBlack on 2007-06-14
Hi,

I've written a script to mount sshfs shares once ssh-add has been performed (to get ssh passphrase). The script works fine except i get a popup message.

'Could not grab keyboard. A Malicious client may be evesdropping on your session.

The Script is as follows.

#!/bin/bash

ssh-add
mount /media/share1
mount /media/share2

Any ideas why this pops up and how to get rid of it?

Thanks

---

### Post by gfixler on 2007-06-15
I'm still pretty much a newb, but the first thing that springs to mind is maybe the script should be owned by root, or run via sudo, or perhaps both. Keep in mind my newbness, though, and that I don't know what dangers, or caveats (i.e. having to sudo to do anything on the mounted shares, as I must do so with my sudo-mounted truecrypt volumes, though I appreciate the extra layer of security there) might apply to something like this with root-level access. Still, if it worked, it would pinpoint for you what's causing the popup.

---

