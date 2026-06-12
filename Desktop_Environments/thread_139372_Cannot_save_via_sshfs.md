---
title: "Cannot save via sshfs"
date: 2006-03-03
forum: Desktop Environments
---

### Post by jgb2185 on 2006-03-03
I've installed sshfs on Breezy, and am puzzled by what I can and cannot do.

I've got identical usernames on my server and my client PC. (Both are running Breezy.) I can mount a server directory on a mount point of my client PC. I can edit and save existing files on the ssh-mounted directories, but I cannot save new files to those folders. Screem, for instance, gives me an 'access denied' error when I try to do a 'save as'. Oddly, though, from the command line on the client PC, I *can* copy new files to the ssh-mounted directories on the server.

I'm not certain if this is a problem with the permissions on the server folders, or some option I've overlooked in sshfs. Any suggestions greatly appreciated.

---

### Post by David A Knight on 2006-03-04
Not sure why it would say access denied, I have never used sshfs or any other fuse base file systems.  Screem can however read/write via ssh itself though as it makes use of gnome-vfs, any ssh server added via the "Connect to Server" functionality of gnome will appear in the file dialog, or press ctrl+L in the save as dialog and type in ssh://server/path/to/folder/to/save/in

---

### Post by jgb2185 on 2006-03-04
Thanks, but I'm using XFCE. I prefer the lighter footprint and better performance, and do not want to switch to Gnome.

I've tried changing the permissions on the server folders to 777, again with no effect. Anybody?

---

