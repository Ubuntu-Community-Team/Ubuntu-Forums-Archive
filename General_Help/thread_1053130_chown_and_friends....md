---
title: "chown and friends..."
date: 2009-01-28
forum: General Help
---

### Post by blackmail on 2009-01-28
I have a question, all the time when i copy some files or folders to my hard drive, ubuntu automatically makes it only available for my root and not for me, and my question is: how do i disable this?because i am tired to chown everything.

---

### Post by jerome1232 on 2009-01-28
They only way that would be happening is if you are copying them as root, just copy them  over as your normal user.

How exactly are you copying these files?

---

### Post by blackmail on 2009-01-29
i just put in the cd and drag an drop them on my little desktop :)
I know that this should be hapening olny if I copy files as root, but i only drag and drop them.I don't know why, that's why i am very confused.
THNX in advance

---

### Post by blackmail on 2009-01-29
oh yes and this is happening only if i copy files, through network or from the cd/dvd rom, but if i download files it does not restrict my rights upon them, and i would really like to disable this function if it is possible.

---

### Post by blackmail on 2009-01-30
i just put in the cd and drag an drop them on my little desktop
I know that this should be hapening olny if I copy files as root, but i only drag and drop them.I don't know why, that's why i am very confused.
THNX in advance
oh yes and this is happening only if i copy files, through network or from the cd/dvd rom, but if i download files it does not restrict my rights upon them, and i would really like to disable this function if it is possible.

---

### Post by jerome1232 on 2009-01-30
When you copy files off a cd they retain their read only attributes, but they are still owned by your user, you have to right click them and set them as writable under the permissions tab. Are the  shares your copying files off of read only as well? Maybe that's what the problem is.

---

### Post by blackmail on 2009-02-03
i tried the permissions thing and it worked, and yes the network wasalso set to write only thnx

---

