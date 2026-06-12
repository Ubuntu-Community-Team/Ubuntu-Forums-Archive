---
title: "DBus error when trying to access NAS"
date: 2012-05-04
forum: Desktop Environments
---

### Post by ElSlunko on 2012-05-04
Hello Everyone,

I'm trying out Deja Dup for the 12.04 cycle and backing up 3TBs of data with it to a NAS. Unfortunately when I try to mount the backup folder I get this error :

```
Sorry, could not display all the contents of "machinabak": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

It seems gvfs is having issue with opening a folder with such a large volume of data in it. When I access the network folder via Windows XP running in a VM it displays just fine.

If all else fails I can go back to using back in time. Thanks for any help you can provide!

---

