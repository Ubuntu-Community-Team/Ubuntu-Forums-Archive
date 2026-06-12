---
title: "/media/usb-cdrom/install: line 1: /lib/libc.so.6: Permission denied"
date: 2005-03-11
forum: Desktop Environments
---

### Post by lorap on 2005-03-11
i run the install script this way:

sudo sh /media/usb-cdrom/install

after what i get immidiatly this error:

/media/usb-cdrom/install: line 1: /lib/libc.so.6: Permission denied
/tmp/6537tmwinstall/install: line 1: /lib/libc.so.6: Permission denied
/tmp/6537tmwinstall/install: /media/usb-cdrom/install: /bin/sh: bad interpreter: Permission denied
/tmp/6537tmwinstall/install: line 300: /media/usb-cdrom/install: Success

please tell me what way i can solve it by.
thanks.
pavel

---

### Post by alastair on 2005-03-11
What is "install"? Find out the file type and perms :

ls -l /media/usb-cdrom/install
file /media/usb-cdrom/install

If it is a text file - open it and have a look.

---

### Post by lorap on 2005-03-11
hi friend!
these're the file's permissions:

-r-xr-xr-x    1 root     root        39499 2004-07-14 08:34 install

i'm trying to install matlab
probably this file isn't permitted to write to the /lib folder
thanks
pavel

---

### Post by vanth13 on 2006-10-02
hello. sorry for my silly question but I'n a new linux user.  I'm tring to run matlab installer doing so:

lucaubu@lucaubu:~/utili/mat/1$ sudo sh ./install -t

Setup aborted . . .
The installer cannot be run when your current directory is on the CD.
Change to the target MATLAB installation directory and rerun the installer.


I copied the files to another directory in my home, but it's the same... ](*,) 

where should I be in the terminal in the destination directory or in the source one? does it make any difference? how can I run this damn installer... I'm loosing many hours on this...
please help...

---

