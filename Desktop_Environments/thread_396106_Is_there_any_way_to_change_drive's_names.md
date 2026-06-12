---
title: "Is there any way to change drive's names"
date: 2007-03-29
forum: Desktop Environments
---

### Post by krussell on 2007-03-29
Hello All :-)

I have been a KDE user, but with Ubuntu i am introduced to Gnome. 
As a new user, i have some trifle questions:
  - How do i change the drive names in "Computer"
  - How do i change the drive icons as well (they are too black-n-white)
  - What is the task manager for Gnome
  - How do i stop the icons showing small "lock" signs for directories i don't have write permission
  - What is the replacement for Karamba (in KDE) in Gnome
  - Why the name of my logical partition (hdb5, vfat) is coming "wwwwwwwww" in Computer?
 
So far, Gnome seems just fantastic! But i am afraid in functionality it is still behind KDE. But the look of Gnome is smooth and soothing than KDE, that's what attracted me most.

Best regards

---

### Post by mcduck on 2007-03-29
> **krussell said:**
> Hello All :-)

I have been a KDE user, but with Ubuntu i am introduced to Gnome. 
As a new user, i have some trifle questions:
  - How do i change the drive names in "Computer"
  - How do i change the drive icons as well (they are too black-n-white)
  - What is the task manager for Gnome
  - How do i stop the icons showing small "lock" signs for directories i don't have write permission
  - What is the replacement for Karamba (in KDE) in Gnome
  - Why the name of my logical partition (hdb5, vfat) is coming "wwwwwwwww" in Computer?
 
So far, Gnome seems just fantastic! But i am afraid in functionality it is still behind KDE. But the look of Gnome is smooth and soothing than KDE, that's what attracted me most.

Best regards

1. For internal partitions this is done by changing the mount point of the partition in /etc/fstab. For removable drives the partition labels are used so changing them changes the name the drive gets when it's mounted.

2. By using some other icon theme. Take a look in /system/Preferences/Theme and [http://www.gnome-look.org/]("http://www.gnome-look.org/")

3. System/Administration/System Monitor

4. Short answer is that you don't, the long is that you could do it by removing the lock icon file or by replacing it with empty transparent picture. I'm not sure where the file is, but most likely somewhere in /usr/share/icons.

5. Try Gdesklets or Adesklets. 

6. the mount point or the partition label would be the most likely reason.

---

### Post by krussell on 2007-03-31
Thanks for the reply. Its a great help. All the problems solved but the names of drives in Computer is still a problem. Changing the names is not changing the drives names. Even my mount point for so called "wwwwwww" is /media/hdb5, but its not coming in Computer.

Thanks again.

---

