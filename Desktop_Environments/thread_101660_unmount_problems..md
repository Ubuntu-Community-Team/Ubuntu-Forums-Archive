---
title: "unmount problems."
date: 2005-12-10
forum: Desktop Environments
---

### Post by Hairy_Palms on 2005-12-10
ive got a minor annoyance with my cd drive, i used to right click on its icon on the desktop and hit eject, and it would work. now it doesnt it says
> umount: only root can unmount /dev/hda from /media/cdrom0
eject: unmount of `/media/cdrom0' failed

its fstab line is
> /dev/hda        /media/cdrom0   udf,iso9660 user,auto     0       0
thanks in advance.
it works if i unmount from the c-line but its an irritation.

---

### Post by aysiu on 2005-12-10
How about this? ```
sudo eject /media/cdrom0
```

---

### Post by Hairy_Palms on 2005-12-10
yes i know that works, but why doesnt the right click menu eject work? im not afraid of the terminal, but opening one to eject a cd is a bit stupid to me.

---

### Post by aysiu on 2005-12-10
[QUOTE=Hairy_Palms]yes i know that works, but why doesnt the right click menu eject work?[/quote] Maybe your /etc/fstab is messed up? This is what my line says ```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
``` What does yours say? Can you post the output of the command ```
cat /etc/fstab
```? 

> im not afraid of the terminal, but opening one to eject a cd is a bit stupid to me. Well, let's get you functioning first--then, worry about what's stupid. If that's the only workaround, you can create a launcher with the command ```
sudo eject /dev/cdrom0
``` to be run in terminal.

---

### Post by Hairy_Palms on 2005-12-10
i already have a launcher. and i already posted the fstab line in my first post there the same but mine is auto
i changed it to noauto and unmounted and remounted but it didnt work

its a gnome problem nothing to do with fstab when i use icewm if i run nautilus i can eject with the right click.

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=Hairy_Palms]ive got a minor annoyance with my cd drive, i used to right click on its icon on the desktop and hit eject, and it would work. now it doesnt it says

its fstab line is

thanks in advance.
it works if i unmount from the c-line but its an irritation.[/QUOTE]
According to the pmount man page, you can't have an /etc/fstab entry for the device if you want it to mount/unmount with pmount/pumount.  I think that is the command Gnome uses to mount/unmount stuff for users, so you could try commenting it out.

---

