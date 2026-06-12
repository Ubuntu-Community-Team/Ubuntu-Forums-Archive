---
title: "ecryptfs private"
date: 2009-04-11
forum: General Help
---

### Post by xpd259 on 2009-04-11
I'm going to do a backup of my /home folder
but each user has their own Private folder using ecryptfs
and I don't want to have to ask each user to move/give me access to their private folder as that defeats the point of Private

I've had a look around my Private with it mounted & unmounted
and i can't see a file or anything where the encrypted data is stored
e.g truecypt/cryptsetup use a file or /dev

its not (as far as i can tell) in any of the .ecryptfs files/folders
so I'm at a loss where it is

any pointers would be fantastic

---

### Post by ushills on 2009-04-11
there should be a hidden .private folder in each /home.

---

