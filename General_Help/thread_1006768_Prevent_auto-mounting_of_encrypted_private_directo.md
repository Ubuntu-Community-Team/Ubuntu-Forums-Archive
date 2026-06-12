---
title: "Prevent auto-mounting of encrypted private directory."
date: 2008-12-09
forum: General Help
---

### Post by wyatt.boi on 2008-12-09
The tutorial the Ubuntu site directs users to does not cover this topic. This is at the bottom of the page:

[quote=https://help.ubuntu.com/community/EncryptedPrivateDirectory]Not covered in this tutorial

    * How the automatic mounting of the encrypted directory works and what files need to be edited to stop the automatic mounting. [/quote]

Pretty much, I want to have to manually mount my private directory when I need to access the files within it. I assume this is a possibility based on the tutorial mentioning it.

Any help would be greatly appreciated! Thanks!

---

### Post by spiderbatdad on 2008-12-09
I'll admit I have not used encrypted private directories, nor followed that tutorial; however, filesystem mounting is generally configured in /etc/fstab

---

### Post by wyatt.boi on 2008-12-09
I looked in the /etc/fstab and didn't find any information for it.
Thanks for the reply though.

---

### Post by spiderbatdad on 2008-12-09
did you not see something similar to :```
mount /dev/loop0 mount point

```
Perhaps an article like this will shed some light on how the filesystem is created and mounted. [http://m.linuxjournal.com/article/6481](http://m.linuxjournal.com/article/6481)

---

### Post by wyatt.boi on 2008-12-09
Yeah, there's no entry in my /etc/fstab for the encrypted private directory. I think that the mounting is done through a PAM auth module when I log in, but I am not sure how to get it to stop, or even find the module...

---

### Post by spiderbatdad on 2008-12-09
how about /etc/mtab?

---

