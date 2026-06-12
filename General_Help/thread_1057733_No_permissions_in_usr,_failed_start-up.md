---
title: "No permissions in usr, failed start-up"
date: 2009-02-02
forum: General Help
---

### Post by Stahlin on 2009-02-02
I did something stupid. I'm not that much of a gamer, and I have been using Linux Ubuntu for about a year now, but I recently decided to install Open Transport Tycoon Deluxe on my PC. Saving the game proved to be impossible, since I did not have the permission to write/edit files in the usr map, where the game is located.

I looked up some things, and I decided to take a look at the permissions, but by accident (sensitive mouse) I clicked on "None" when editing the permissions as root, which was not my intention. The consequences are however that I do not longer have access to the usr map. Letters turned to squares, icons turned to X's and I decided to reboot my PC. At start-up I almost panicked when I saw that I could no longer start Ubuntu because the permission was denied. Even when I start up in recovery mode, permission is still denied. What am I to do?

---

### Post by heindsight on 2009-02-02
Hopefully you did not recursively change the permissions, in which case you can boot from a live CD, open a terminal and do:

```
sudo mount /dev/sdaX /mnt
sudo chmod 555 /mnt/usr
sudo umount /mnt
```

Replace sdaX with the partition containing your root filesystem.

If this doesn't fix things, then you probably did a recursive change of permissions, in which case you'll have your work cut out for you, manually resetting the permissions of every file under /usr. If that's the case, it might be advisable to reinstall...

---

### Post by Stahlin on 2009-02-02
To my dismay I noticed that sudo doesn't work.

---

### Post by heindsight on 2009-02-02
If you boot from a live CD it should work, since then you're not relying on anything from your broken installation.

---

### Post by Stahlin on 2009-02-02
It doesn't work. I have copied all my important files, and am reinstalling now. Thank you for your help.

---

