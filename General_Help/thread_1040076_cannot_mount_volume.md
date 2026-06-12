---
title: "cannot mount volume??"
date: 2009-01-15
forum: General Help
---

### Post by Kaneda187 on 2009-01-15
I get this pop up when i try to mount my xp partition. 
```
Unable to mount 60.0 GB Media

DBus error org.freedesktop.DBus.Error.NoReply: 
Did not receive a reply. Possible causes include: 
the remote application did not send a reply, 
the message bus security policy blocked the reply, 
the reply timeout expired, or the network 
connection was broken.
```

any ideas?

---

### Post by Kaneda187 on 2009-01-16
anybody??

---

### Post by mtausig on 2009-01-16
Give a bit more details, please.
What command did you issue, that gave you this error message?
What is the content of your /etc/fstab?

---

### Post by morbid_bean on 2009-01-16
I have the same exact problem...  [http://ubuntuforums.org/showthread.php?t=1040969](http://ubuntuforums.org/showthread.php?t=1040969)      it will do this after selecting the hard drive off the places menu.

---

### Post by Kaneda187 on 2009-01-16
it wasn't a command line. i just put that code thing ther to illustrate the pop up window that i got. so any ideas? it happens when i try to mount it>places>60.0GB Media 
then i get this

Cannot mount volume.
You are not privileged to mount this volume.

then this

Unable to mount 60.0 GB Media
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by TheMyself on 2009-01-16
The XP partition might not be properly shot down (like if you hibernate it.) Install "NTFS configuration tool". It helps with the privilege problem. (You must mount volumes as root; the configuration tool helps with that. )

---

### Post by Kaneda187 on 2009-01-17
yep that was the problem i figured it out after i left the post! thanks anyways!! what happened the thanks button and wher'd my thanks go??

---

