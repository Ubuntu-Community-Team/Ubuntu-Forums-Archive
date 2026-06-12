---
title: "how to hook script to be run just before USB media removal"
date: 2010-06-21
forum: Desktop Environments
---

### Post by mafeusek on 2010-06-21
Hallo.
I need to perform non-root command just before USB media is removed.

Have You got any ideas?

best regards,
Pawel

---

### Post by ajgreeny on 2010-06-21
Give us lots more detail about what you are trying to do, and I'm sure many will attempt to help you, but there is not enough information at the moment.

---

### Post by mafeusek on 2010-06-21
> **ajgreeny said:**
> Give us lots more detail about what you are trying to do, and I'm sure many will attempt to help you, but there is not enough information at the moment.

sorry for giving too little details.

I have truecrypt volume file on my usb pen drive.
when USB is being removed I want "truecrypt -d /path/to/volume/file" command be performed.

that's it.

Additionally I wonder if removable medias are automatically unmounted at user logout and if user is being logged out automatically when system is going to be shut down?

best regards,
Pawel

---

### Post by ajgreeny on 2010-06-24
I can't help with the first part of your query, but regarding the second, a usb drive will not be unmounted when you logout, as far as I'm aware.  Only when you shutdown, then it certainly will unmount properly, as will all other mounted drives.

---

