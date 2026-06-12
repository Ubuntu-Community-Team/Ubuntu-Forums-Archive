---
title: "Grub default disk edit"
date: 2005-10-27
forum: Desktop Environments
---

### Post by VTX on 2005-10-27
I have read how to edit the /boot/grub/menu.1st file and I understand the procedure.
when I go directly to the file from the drive it will not give me permission to edit the file ( I want to change the default boot to XP) I am new to this so be very specific please. I have Konsole app on my system but I am not to informed on how to use it.

---

### Post by Ampersand on 2005-10-27
You need to edit it as root. To do this, run sudo followed by whatever text editor you're using, eg
```
sudo kwrite /boot/grub/menu.1st
```
or
```
sudo nano /boot/grub/menu.1st
```

---

### Post by VTX on 2005-10-27
[QUOTE=Ampersand]You need to edit it as root. To do this, run sudo followed by whatever text editor you're using, eg
```
sudo kwrite /boot/grub/menu.1st
```
or
```
sudo nano /boot/grub/menu.1st
```[/QUOTE]

What text editior am I using? where do I find it?

---

### Post by Ampersand on 2005-10-27
If you open a terminal (Konsole if you're using KDE), and type

```
sudo nano /boot/grub/menu.1st
```

a text editor program will open in the terminal (similar to Ed in ms-dos). Make the necessary changes to the file, then press Ctrl and O to save, then Ctrl and X to exit.

Alternatively, if you want to use a notepad-like editor, use the same command, but replace nano with kwrite (if you're using KDE) or gedit (if you're using gnome).

---

### Post by julianbury on 2005-10-28
That won't work for me.

I opened Terminal and wrote ...

sudo gedit /boot/grub/menu.1st

gedit opens empty.

If I use its file-open and navigate to menu.1st, it will not allow editing.

Is this because I have installed ubuntu 5.10 ?

---

### Post by doina100 on 2005-10-29
the file to edit  is menu.**l**st     that is l as in list not 1 as in the number.

---

