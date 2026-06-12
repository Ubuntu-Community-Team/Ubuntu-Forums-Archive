---
title: "rTorrent and Permissions"
date: 2008-12-15
forum: General Help
---

### Post by ecfitzgerald on 2008-12-15
I have rTorrent running and its great, the only caveat is trying to work with the files from Windows.

I can copy the files from my "finished" directory, but I can't delete the files in the "finished" directory.

Could I add another on_finished line?  But what is the portion right after that?
there is rm_torrent, and mv_finished.  They both use $d, so I assume rtorrent knows what rm_torrent and mv_finished are, to put the correct files names in place.

An archived thread with this same question never got an answer, but suggested its a Samba config issue, which doesn't make sense to me, as when I make the copy through samba the permissions are correct as to the create mask I have.  Its the permissions rTorrent uses.

---

### Post by Nepherte on 2008-12-15
Doesn't mv_finished moves the files (i.e. remove the file from the original place and put it in the target directory)? That means you don't have to remove it since it doesn't exist in the original directory anymore. I could be wrong though.

---

### Post by ecfitzgerald on 2008-12-15
You are right it does.  Let me explain what I have a bit further.

/rtorrent/active/  holds torrents and the downloading files
/rtorrent/finished/ this is where they get moved when they are done, by the on_finished=mv_finished line.
I then, from windows via smb, copy the files to the media server directories I have.  Because the rtorrent files are read only to group/world I can only copy them to the final directories.

---

