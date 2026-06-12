---
title: "problem in konqueror with view option on media:/ with inode/directory call"
date: 2006-08-21
forum: Desktop Environments
---

### Post by wildblue on 2006-08-21
hello.
i have an problem that i cant solve my self.
i searched different forums and also searched in google for any help.

i am going to open my konqueror in media:/
if i open it in /media/ everything with the detailed view (that is saved in the profile) is ok.

only when i open media:/ and klick on any device the symbols are not in detailed view. they are icons.

when i load my profile (filemanagement) everything is in detailed view.

i know, when i klick on any device
an inode/directory call is done
the shortcut to these call is in kfmclient_dir.desktop under  /usr/share/applications/kde/.
i tryed changing the execute string in this file with
openProfile filemanagement in line
Exec=kfmclient openProfile filemanagement %u inode/directory-
but nothing happened.

who can help? also in german language...

---

