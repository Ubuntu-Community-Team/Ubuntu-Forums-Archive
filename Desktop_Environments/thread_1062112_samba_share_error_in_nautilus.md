---
title: "samba share error in nautilus"
date: 2009-02-06
forum: Desktop Environments
---

### Post by akuneko on 2009-02-06
first of all, my error is similar to the thread [http://ubuntuforums.org/showthread.php?t=141073](http://ubuntuforums.org/showthread.php?t=141073)

1) my computer spontaneously shutdown while i was in the middle of using nautilus to browse a samba share.  when i rebooted, nautilus could no longer open any audio/video files from a samba share.  also, my samba shares used to temporarily create a link in ~/.gvfs/<smb mount> but now it does not anymore whenever i mount via "smb://<samaba mount>".  i tried reinstalling all gvfs components and nautilus but still no change.

[IMG]http://img22.imageshack.us/img22/3918/failopenup0.png[/IMG]

when i mount manually without gnome the files will open.
```
mount -t smbfs -o username=###,password=### //server/folder /mnt/temp
```

2) in addition to the samab error, nautilus will no longer mount/unmount any volumes in the places side panel when i click on a drive or even when i try to use the right click menu.

any suggestions?  is there some module that may have been corrupted from the sudden comp shutdown?

---

### Post by mjheagle8 on 2009-02-06
did you purge the gvfs when you reinstalled it? otherwise the settings would remain.

---

### Post by akuneko on 2009-02-06
purging + reinstalling didn't work either

---

### Post by mjheagle8 on 2009-02-07
did you do this with every gvfs and samba file? and dont let synaptic auto mark packages. did you purge EVERY one of these?

---

