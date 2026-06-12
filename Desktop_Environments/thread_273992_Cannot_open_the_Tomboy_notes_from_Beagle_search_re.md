---
title: "Cannot open the Tomboy notes from Beagle search results"
date: 2006-10-09
forum: Desktop Environments
---

### Post by ametade on 2006-10-09
Hi,

I'm using Edgy Eft.

When searching using beagle-search, I can't open the tomboy notes from the
search results. The note doesn't get displayed. Nothing happens.

The same thing occurs with the deskbar-applet configured to use the
"Live Beagle Search". When you click on a tomboy note result, the note
doesn't get displayed.

The following error occurs executing beagle-search at the terminal:
```
Unhandled Exception: System.ApplicationException: Name 'com.beatniksoftware.Tomboy' does not exist.
 at DBus.Service.Get (DBus.Connection connection, System.String name) [0x00000]
 at Tomboy.RemoteControlProxy.GetInstance () [0x00000]
 at Tomboy.TomboyCommandLine.Execute () [0x00000]
 at Tomboy.Tomboy.Main (System.String[] args) [0x00000]
```

I've filled a bug at:
[https://launchpad.net/distros/ubuntu/+source/beagle/+bug/63939](https://launchpad.net/distros/ubuntu/+source/beagle/+bug/63939)

Does anybody has the same problem?

---

### Post by kwalo on 2006-10-09
I had similar problem with indexing file system. It was caused by an unexpected system crash. After that my index got broken, so I killed beagled and beagled-helper processes and removed ~/.beagle directory. That caused beagle to rebuild all Indexes and everything works fine since then.

---

### Post by ametade on 2006-10-09
> **kwalo said:**
> I had similar problem with indexing file system. It was caused by an unexpected system crash. After that my index got broken, so I killed beagled and beagled-helper processes and removed ~/.beagle directory. That caused beagle to rebuild all Indexes and everything works fine since then.

Hi kwalo, thanks for the information but it didn't worked :(

I don't have a problem with the indexes: everything is indexed properly. The problem is that when searching for something at beagle-search I cannot open tomboy's search results. 

I can open everything else (images, folders, openoffice documents, etc.) by double clicking it, but it doesn't work with tomboy's notes. When I double click on a tomboy note at beagle-search I get the error I mentioned at my first post.

---

### Post by kwalo on 2006-10-09
Sorry I thought it's an indexing issue ](*,) 

Anyway I can't open notes from beagle, when tomboy is closed (not in tray), bu if I launch it I can access notes from beagle search results. I've confirmed your bug on launchpad.

---

### Post by ametade on 2006-10-09
Thanks, once again!

I have tomboy running at the top panel and I get the first error. I tried to remove tomboy, executing it at the terminal, but I still can't launch the notes from the search results.

Maybe it is something related to my tomboy installation. I've to check it out.

---

### Post by kwalo on 2006-10-10
I guess this discussion should be continued on launchpad.
(The bug you've submitted).

---

