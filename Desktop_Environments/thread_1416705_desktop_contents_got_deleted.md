---
title: "desktop contents got deleted"
date: 2010-02-26
forum: Desktop Environments
---

### Post by daudiam on 2010-02-26
I typed the following in the terminal to mount my pendrive onto the desktop
```
sudo mount /dev/sdb1 /home/waqas/Desktop/
```when I went into my desktop again there was nothing but the pen drive. Even after umounting the pen drive, the contents of the desktop did not return. Where are they ?

---

### Post by Kakers on 2010-02-26
Type the following to see if they are still there:

```
cd ~/Desktop
ls -l
```

---

### Post by daudiam on 2010-02-26
Yes, thankfully they are. But, how to get them to show on the desktop ?

---

### Post by Kakers on 2010-02-26
I've had this kind of problem before with stuff not showing up on the desktop, I can't remember how I fixed it... may have been just a restart, but you should be able to move them out of your desktop to something like ~/  then see if they show up... if they do then move them back to ~/Desktop

---

### Post by daudiam on 2010-02-26
Thanks. It worked when I restarted but why didn't it show when I mounted the pendrive on the Desktop. When I went into the Desktop folder via the GUI, it didn't show anything. But by typing to cd ~/Desktop, the contents were shown. Why was that ?

---

### Post by Kakers on 2010-02-26
Maybe because it opens up the USB stick onto the desktop rather then putting into  a folder you could probably do:

```

cd ~/Desktop
mkdir /usb
mount /dev/sdb1 ~/Desktop/usb
```

That should then mount it to the folder USB. also I may be wrong but I think usb sticks are hda ? to confirm you could type 'sudo fdisk -l'

---

