---
title: "Is this possible? 2 networked ubuntu comps"
date: 2006-04-25
forum: Desktop Environments
---

### Post by bionnaki on 2006-04-25
greetings. I have two computers networked together to a wireless linkysys router. Is it possible for both computers to access a particular directory on each computer (respective music/media directories)? If so, how exactly can I set this up? thanks!

---

### Post by gerbman on 2006-04-26
Yup, with [Samba]("https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29")! Should do the trick for ya.

---

### Post by gerbman on 2006-04-26
Guess I didn't read the guide myself...apparently you don't need Samba to do it, only NFS. But I've not used NFS. Samba will work, though it might be more work than is needed. [Here's]("https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28up%29%7C%28setting%29%7C%28nfs%29") an NFS guide. I'm probably just used to Samba, but NFS looks like more work.

---

