---
title: "How do you add sshfs bookmarks to Dolphin like in nautilus?"
date: 2013-04-01
forum: Desktop Environments
---

### Post by vfclists on 2013-04-01
How do you add sshfs bookmarks to Dolphin like in Nautilus?

I am referring to the way FTP and SSHFS shortcuts created from the Places dialog are added to Nautilus screen.

I am interested in the KDE equivalent of that in Ubuntu 12.04.

---

### Post by SeijiSensei on 2013-04-01
Use a "fish" URL, e.g., fish://server/ or fish://server/share/.  The URL standard also allows a username like fish://joe@server/home/joe/ to reach joe's home directory.  Once you've set up the connection to the server or share, just drag the item into the column of favorite places inside Dolphin.  I find this very convenient when I want to upload content to my web server from my KDE desktop.

Dolphin also supports smb://user@server/share/ URLs to connect to remote Windows machines or Linux servers running Samba.

---

### Post by vfclists on 2013-04-03
Thanks for the reply.
Is it possible to map a fish location into a directory like in sshfs?

---

### Post by SeijiSensei on 2013-04-03
You can permanently set up a sshfs mount by adding an entry to /etc/fstab.  I don't do this myself, but [this post](http://ubuntuforums.org/showthread.php?t=430312) looks promising.

Otherwise, as I said, you can drag and drop the fish-mounted directory into the favorites panel on the left side of the Dolphin interface.

---

