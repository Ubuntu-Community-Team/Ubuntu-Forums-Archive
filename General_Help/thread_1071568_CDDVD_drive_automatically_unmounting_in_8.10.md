---
title: "CD/DVD drive automatically unmounting in 8.10"
date: 2009-02-16
forum: General Help
---

### Post by cor2y on 2009-02-16
I have noticed in 8.10 that my dvd drives automatically mount and unmount by themselves, for example after a few hours on discs in the drives will mysteriously disappear off the desktop and ejecting and inserting again yields nothing in nautilus , i get an error about "unable to mount media no disc in drive" or a dbus /Hal error "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

However after a few hours suddenly the drive will be mounted again, trying to mount manually from the terminal causes the drive that has the disc in it to hang
```

sudo mount /dev/scd0


```
Thats what the terminal displays nothing that the mount failed or that it was successful.
The only recourse usually requires a reboot.
Its very frustrating because there is no rhyme or reason to it.
Sometimes i may want to listen to a music cd, watch a dvd or burn something to dvd/cd and the discs don't get recognized when inserted as being in the drive.
This is the first time this has happened , it never happened in earlier versions of ubuntu so it must be 8.10 specifc.

---

