---
title: "create a shortcut to the mounted windows partition"
date: 2010-06-01
forum: Desktop Environments
---

### Post by cccc on 2010-06-01
hi

I have Ubuntu 10.04 with Gnome installed on a dual boot machine with Windows XP.
Howto create a desktop shortcut to the mounted windows vfat partition?
The /etc/fstab entry for the windows partition is already done.

---

### Post by chiliman on 2010-06-01
i think what you are looking for is in this thread

[http://ubuntuforums.org/showthread.php?t=1298488&highlight=mount+windows+shares+bootup](http://ubuntuforums.org/showthread.php?t=1298488&highlight=mount+windows+shares+bootup)

---

### Post by cccc on 2010-06-01
Thx, but I know howto mount a windows partition.
I'd like to create a shortcut to the mounted partition on the Gnome desktop.

---

### Post by chiliman on 2010-06-02
according to this
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)  

you should be able to change your mount point to
/home/"username"/Desktop/  
i would give it a try im fairly sure that will give you what you want, i hope[-o<.   otherwise sorry if i couldn't be much more help:neutral:.

---

### Post by cccc on 2010-06-02
That's not what I want.

/etc/fstab entry for the windows partition is already done.

I'd like to create just a desktop shortcut to the already mounted windows partition.

---

### Post by Little Bones on 2010-06-02
If you go into gconf, then apps->nautilus->desktop, it should show a thing there with a checkbox, saying 'volumes visible'. Check that off if it isn't, that says that any mounted drives will be shown on the desktop. That's one way I know of.

---

### Post by nerdzero on 2010-06-02
cccc, right-click on the Desktop and select "Create Launcher..."

Change the Type from Application to Location.

Enter whatever you like in the Name field, "Windows Share" for example.

Enter the path to the mount location in the Location field such as "/mnt/windows" or "/media/shared_folder".

Click the Icon to change it to something else if you want otherwise hit OK and you are good to go.

---

