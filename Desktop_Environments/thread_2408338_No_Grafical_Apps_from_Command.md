---
title: "No Grafical Apps from Command"
date: 2018-12-17
forum: Desktop Environments
---

### Post by coltvas on 2018-12-17
Hello everybody
One day I couldnt run nautilus from command...
the error is:

ulises@XXXXX:~$ sudo nautilus
[sudo] contraseña para ulises: 
Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: No se pudo conectar: Conexión rehusada


(nautilus:11627): Gtk-WARNING **: 12:12:35.916: cannot open display: :0
ulises@XXXXX:~$ 




anyway...  I cant run anything form command, but naulitus is the only one i need.

pls help

Ubuntu 18.04LTS

---

### Post by Frogs Hair on 2018-12-17
Running sudo nautilus can cause problems with the file system . Have you been doing this regularly ?

---

### Post by coltvas on 2018-12-17
Yes ... since 2012 ...
on 14, 16 and now on 18.
actually I did a clean installation on 18.04 LTS and worked ok till 2 weeks ago.

---

### Post by Frogs Hair on 2018-12-17
You may have some corruption . You can try the following command ,but please read post 118 from the link.

[https://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications](https://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications)



```
sudo -H nautilus   
```

---

### Post by coltvas on 2018-12-17
Still with the problem...

I Use a lampp server and all the files are in the htdocs folder wich is "editable" only with nautilus to create folders and files to edit them ... 
i'll try to move the folder to my /HOME so nautilus wont be needed.

this is the command prompt:

ulises@XXXXX:~$ sudo rm ~/.Xauthority
ulises@XXXXX:~$ sudo nautilus
No protocol specified
Unable to init server: No se pudo conectar: Conexión rehusada


(nautilus:14880): Gtk-WARNING **: 14:20:07.834: cannot open display: :0
ulises@XXXXX:~$ sudo -H gedit
No protocol specified
Unable to init server: No se pudo conectar: Conexión rehusada


(gedit:14888): Gtk-WARNING **: 14:20:12.554: cannot open display: :0
ulises@XXXXX:~$ sudo -H nautilus
No protocol specified
Unable to init server: No se pudo conectar: Conexión rehusada


(nautilus:14894): Gtk-WARNING **: 14:20:17.617: cannot open display: :0
ulises@XXXXX:~$

Im not ubuntu/linux expert but looks like terminal cant connect to the graphical apps.

---

### Post by ajgreeny on 2018-12-17
Perhaps ownership of folders and files in your home has been changed to root, as that is what using command **sudo nautilus** can do to them all; they should all belong to you as user.

Let's see the output of ```
ls -la
``` in terminal.
Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**

---

### Post by coltvas on 2018-12-17
ok, sorry output:
```

ulises@VasUB:~$ ls -la
total 208
drwxr-xr-x 30 ulises ulises  4096 dic 17 14:19 .
drwxr-xr-x  4 root   root    4096 may 24  2018 ..
-rw-------  1 ulises ulises  5219 dic 10 23:38 .bash_history
-rw-r--r--  1 ulises ulises   220 may 24  2018 .bash_logout
-rw-r--r--  1 ulises ulises  3815 nov 26 10:43 .bashrc
drwx------ 32 ulises ulises  4096 nov 26 12:52 .cache
drwx------  3 ulises ulises  4096 may 24  2018 .compiz
drwx------ 36 ulises ulises  4096 dic 17 14:10 .config
drwx------  3 root   root    4096 may 24  2018 .dbus
drwxr-xr-x  2 ulises ulises  4096 nov 26 15:51 Descargas
-rw-r--r--  1 ulises ulises    25 may 24  2018 .dmrc
drwxr-xr-x  2 ulises ulises  4096 nov 26 15:52 Documentos
drwxrwxr-x  2 ulises ulises  4096 jul 17 21:47 dwhelper
drwxr-xr-x  3 ulises ulises  4096 ago 10 09:10 Escritorio
-rw-r--r--  1 ulises ulises  8980 may 24  2018 examples.desktop
drwx------  2 ulises ulises  4096 ago 10 15:37 .gconf
drwxr-xr-x 24 ulises ulises  4096 ago 27 14:56 .gimp-2.8
drwx------  3 ulises ulises  4096 may 24  2018 .gnome
drwx------  3 ulises ulises  4096 may 28  2018 .gnupg
drwxr-xr-x  2 ulises ulises  4096 jul 26 16:45 .gphoto
drwx------  2 root   root    4096 may 28  2018 .gvfs
-rw-------  1 ulises ulises 31400 dic 17 10:25 .ICEauthority
drwxr-xr-x  2 ulises ulises  4096 nov 26 11:05 Imágenes
drwx------  3 ulises ulises  4096 may 24  2018 .local
drwx------  5 ulises ulises  4096 may 24  2018 .mozilla
drwxr-xr-x  2 ulises ulises  4096 may 24  2018 .multisystem
-rw-r--r--  1 ulises ulises     6 may 24  2018 .multisystem-theme
drwxr-xr-x  2 ulises ulises  4096 may 24  2018 Música
-rw-------  1 ulises ulises  1083 may 28  2018 nohup.out
drwx------  3 ulises ulises  4096 may 24  2018 .pki
drwxr-xr-x  2 ulises ulises  4096 may 24  2018 Plantillas
-rw-r--r--  1 ulises ulises   679 may 24  2018 .profile
drwxr-xr-x  2 ulises ulises  4096 may 24  2018 Público
drwx------  3 ulises ulises  4096 dic 17 10:27 .putty
drwx------  2 ulises ulises  4096 dic 17 10:34 .remmina
drwxr-xr-x  5 ulises ulises  4096 nov 26 10:36 snap
drwx------  2 ulises ulises  4096 may 28  2018 .ssh
-rw-r--r--  1 ulises ulises     0 may 24  2018 .sudo_as_admin_successful
drwx------  3 ulises ulises  4096 ago  6 10:55 .thumbnails
drwxr-xr-x  2 ulises ulises  4096 may 24  2018 Vídeos
-rw-------  1 ulises ulises  1633 may 28  2018 .xsession-errors
-rw-------  1 ulises ulises  1384 may 28  2018 .xsession-errors.old
ulises@VasUB:~$ 



```

---

### Post by ajgreeny on 2018-12-17
I assume your username on that machine is ulises, and if so I think your problem is that the two files, .gvfs and .dbus, are both owned by root, probably because you have been using command **sudo nautilus**.

You should be able to change ownership of those two files from recovery mode (from the grub menu), choosing "Root shell" from the menu that appears.
Recovery mode is command line only, and by default mounts the filesystem read only so firstly you need to run command ```
mount -o rw,remount /
``` to remount it read/write then run commands ```
chown ulises:ulises /home/ulises/.gvfs
chown ulises:ulises /home/ulises/.dbus
```
No sudo is needed as you are already running as root in Recovery mode.

Now reboot and hopefully you will get into the usual GUI you expect.
Remember now to **NEVER USE sudo nautilus** again.

---

