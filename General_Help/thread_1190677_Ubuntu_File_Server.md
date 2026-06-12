---
title: "Ubuntu File Server"
date: 2009-06-18
forum: General Help
---

### Post by ninos_loves_u@hotmail.com on 2009-06-18
i have 2 laptops and 1 desktop (one of the laptop has dual-boot with xp) they are all conntected to the internet thru wireless router (all on wireless connction not Ethernet) is there way which i can connect all the PCs together for file sharing so if i login to any1 of them i can browse all the files on the other computers???? please provide step by step instructions or a link thanks

---

### Post by ninos_loves_u@hotmail.com on 2009-06-18
i have 2 laptops and 1 desktop (one of the laptop has dual-boot with xp) they are all connected to the internet thru wireless router (all on wireless connection not Ethernet) is there way which i can connect all the PCs together for file sharing so if i login to any1 of them i can browse all the files on the other computers???? please provide step by step instructions or a link thanks

---

### Post by swerdna on 2009-06-18
Should I answer on this post: [http://ubuntuforums.org/showthread.php?p=7477063#post7477063](http://ubuntuforums.org/showthread.php?p=7477063#post7477063)
or should I answer on this post: [http://ubuntuforums.org/showthread.php?p=7477077#post7477077](http://ubuntuforums.org/showthread.php?p=7477077#post7477077)

Let me know so I don't make a duplicate, because duplicates are very confusing.

---

### Post by swerdna on 2009-06-18
Should I answer on this post: [http://ubuntuforums.org/showthread.php?p=7477063#post7477063](http://ubuntuforums.org/showthread.php?p=7477063#post7477063)
or should I answer on this post: [http://ubuntuforums.org/showthread.php?p=7477077#post7477077](http://ubuntuforums.org/showthread.php?p=7477077#post7477077)

Let me know so I don't make a duplicate, because duplicates are very confusing.

---

### Post by 3rdalbum on 2009-06-18
Yes, you certainly can.

Right-click on the folder you want to share, and choose Properties. Click the Share tab. Click "Share this folder", set a name for the share, and click Create Share. You may be prompted to install some Samba packages - let it.

From the other computers, you can then go to Places > Network and your first share should show up. To access the share, you will need to specify the username and password from the server.

Due to some problems in Gnome you might need to reboot the server and the prospective client machine before they will see eachother. Make sure that the server machine is up and running before the client starts up.

If you want more control (for instance, to create an invisible share or allow users to log into your share with their own user accounts, rather than using your user account) you can install the "system-config-samba" program.

Note that I set up my last two Samba shares using system-config-samba and the previous one "manually" by editing the Samba configuration file, so I can't promise that the first method will work properly. If you use system-config-samba it will work.

EDIT: You can edit your posts on this forum to correct spelling mistakes.

---

