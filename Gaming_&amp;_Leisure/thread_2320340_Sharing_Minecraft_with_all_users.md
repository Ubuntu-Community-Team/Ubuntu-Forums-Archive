---
title: "Sharing Minecraft with all users"
date: 2016-04-13
forum: Gaming &amp; Leisure
---

### Post by jonesy3 on 2016-04-13
Just switched to Ubuntu 14.04 from WinXP yesterday; so, I have much to learn. While I am, however, I'm trying to get Minecraft reinstalled for my son.
I followed the above steps and had no problem getting the game going - on MY account.
But, when I switched to his account to TRY the suggestions on creating a desktop icon launcher, Minecraft wasn't even available.
The jar file is in MY downloads folder but his folder is empty.
I certainly don't want 2 installations; so, is there a way to share it? Move it to a shared folder (I tried moving it to the Games folder but was told permission is denied)? Or, should I uninstall on my account and install on his?
I would really rather share it to all users.
Any help is appreciated; but, please keep in mind I have only a few hours experience with Ubuntu. I just don't want him to have to wait months while I learn the system.
Thanks!

---

### Post by mastablasta on 2016-04-13
you need to make the folder accessible to all users. at the moment only your user has the right to access it.

about permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

then you have two options: [http://askubuntu.com/questions/487527/give-specific-user-permission-to-write-to-a-folder-using-w-notation](http://askubuntu.com/questions/487527/give-specific-user-permission-to-write-to-a-folder-using-w-notation)

these are possible to do in file manager if you start it with root permissions.

might be simpler to move it to outside folder, create minecraft group that will own the folder, and add all users, that will play, it to that group.

I am not sure minecraft is really installed in Linux. it's just unpacked and run if I remember correctly.

---

### Post by jonesy3 on 2016-04-13
Moving it is denied. But, realizing it's unpacked and run rather than installed leads me to a fresh download into a shared folder.
Thank you.

---

### Post by oldrocker99 on 2016-04-13
And now you know just how useful this forum can be. Welcome to fun computing!

---

