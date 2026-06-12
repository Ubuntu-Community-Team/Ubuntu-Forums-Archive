---
title: "hibernation button disappeard"
date: 2008-10-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Beela on 2008-10-04
Hi,
my inspiron 6400 carrying ubuntu 8.04 used to have a problem with hibernation, the swap space was not enough, so i have been advised to increase that size and that what i did. opening new file and mount that file with the existing swap. once i restart my computer to put this changes on, swap size is increased. however, I have been disappointed when i realized that hebirnate button on quit has been disappeared. so please if any one could help i will appreciated.
Thanks

---

### Post by niteshifter on 2008-10-05
Hi,

Could you post the output of the below command:
```
cat /proc/swaps
```
please?

---

### Post by jamesrl on 2008-10-05
Run (Alt-F2) gconf-editor
From there search (Ctrl-F) for hibernate allowing searching key value names.  Go to /apps/gnome-power-manager/general/can_hibernate and make sure its checked (meaning set to true).
Or if you prefer the commandline run:
```

gconftool-2 --set /apps/gnome-power-manager/general/can_hibernate --type=bool true

```

---

### Post by SteveMcQwark on 2008-10-06
I have the same situation:
cat /proc/swaps returns:
```
Filename				Type		Size	Used	Priority
/mnt/4Gb.swap                           file		4194296	0	-1 
```

and can_hibernate is checked.

---

