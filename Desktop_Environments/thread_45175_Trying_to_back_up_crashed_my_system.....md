---
title: "Trying to back up crashed my system...."
date: 2005-06-29
forum: Desktop Environments
---

### Post by escobar on 2005-06-29
Here's the short version of what happened:

I tried backing up my system using the how to in the Tips in Trick session. While the backup was being performed I got an error saying my HD is out of space. This isn't so because I have over 50GB free but I thought no big deal. For whatever reason Ubuntu started acting weird, intermittent freezing and all so I think again it's no big problem I'll restart and remove the backup file. Well Ubuntu doesn't agree. When trying to log in it will just sit there with a brown background. Nothing else. Here's what I have at my disposal:

The Ubuntu Live CD, that I'm currently using to type this :grin: 

And Windows XP Pro, which is still fully functional. Can anyone help?

---

### Post by angkor on 2005-06-29
Just an idea, but how much free space do you have in / ?

---

### Post by escobar on 2005-06-29
After the failed backup, I have none. Before I re-booted into this problem it showed 0 bytes free, but the size of the backup was only about 1GB when I looked at the properties for it. 

Does this mean I have to reinstall?

---

### Post by escobar on 2005-06-29
Bump.

Can anyone assist? I really need help. Thanks

---

### Post by cwaldbieser on 2005-06-29
From the LiveCD, can you just mount your hard drive and erase the backup file?

---

### Post by escobar on 2005-06-30
Heh, I booted into to receovery mode and typed "rm- rf backup.tgz" 

Rebooted and that did it. Thanks a mil, I really didn't want to reinstall. Now I have to figure out what I did wrong.

---

### Post by angkor on 2005-07-01
You have to make sure / has space free in order for you system to function. If root doesn't have any more space your system will *crack*.

---

