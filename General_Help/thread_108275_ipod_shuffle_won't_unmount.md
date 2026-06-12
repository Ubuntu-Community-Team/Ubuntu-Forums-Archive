---
title: "ipod shuffle won't unmount"
date: 2005-12-25
forum: General Help
---

### Post by oldmanstan on 2005-12-25
I bought an ipod shuffle and i can use gtkpod just fine to put music on it and whatnot but when i right click on the desktop icon and click the unmount item the icon goes away then nothing then after about 30 seconds and error message pops up saying it can't unmount the thing. I tried having gtkpod handle mount/unmount but same problem basically just with gtkpod error messages.

Anybody know how to solve this little problem? I have to unmount it cuz when i just pull it out it screws up and wont play.

---

### Post by kaamos on 2005-12-25
DISCLAIMER: Never owned an ipod.

The unmounting probably needs the -l switch (force umount). So if there is no way to insert this to gtkpod, you can alway unmount it manually by: "sudo umount -l /dev/**xxx**"

If you're not shure where the ipod is mounted, use the command "mount". Hope this is of some use..

---

### Post by aysiu on 2005-12-25
I've found ```
sudo eject /dev/sda1
``` to be the most effective means to eject iPods if something's wrong. Of course, it could be /dev/sde1. Type ```
sudo fdisk -l
``` to be sure.

---

### Post by mcduck on 2005-12-25
i use 'sudo eject ipod' with my mini ;)

---

### Post by oldmanstan on 2005-12-25
Thanks for the feedback all! I can now unmount it just fine. Now i'm just waiting on a stable app to manage the songs on it... gtkpod won't access the DB file on the ipod, amarok crashes when i try to transfer songs and banshee freezes when i transfer songs (luckily it freezes AFTER it transfers them but it's still a really ugly process to go through)

---

### Post by lapsey on 2006-01-11
[QUOTE=oldmanstan]Thanks for the feedback all! I can now unmount it just fine. Now i'm just waiting on a stable app to manage the songs on it... gtkpod won't access the DB file on the ipod, amarok crashes when i try to transfer songs and banshee freezes when i transfer songs (luckily it freezes AFTER it transfers them but it's still a really ugly process to go through)[/QUOTE]

try the shuffle db builder instead. [http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/) 


at just 1 standalone python script it is lightweight and brilliant. shuffles shouldn't need syncing or library management anyway.

---

