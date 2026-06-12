---
title: "gvfs will not always reply"
date: 2008-05-26
forum: Desktop Environments
---

### Post by pokkys on 2008-05-26
Since Ubuntu use 'fuse' to mount sftp,smb,and ftp under $HOME/.gvfs , I notice the "OPEN with ...." will use $HOME/.gvfs  intend of smb://xxxx .
This is a good idea to avoid app like "mplayer" to be rewrote to read smb:// over gnome auth.But sometimes, $HOME/.gvfs will not always works.And then nautilus reply "smb://" after fail try of .gvfs (but it do works). Is there someone notice the bug ?

And there is no pitfdll of amd64, so that totem-gstreamer cannot play "rmvb" over smb:// any more.

---

