---
title: "Can't Edit GRUB"
date: 2008-12-15
forum: General Help
---

### Post by eweb100 on 2008-12-15
When i do This 

gksudo gedit /boot/grub/menu.lst

 in root i get this

eric@eric-desktop:~$ su
Password: 
root@eric-desktop:/home/eric# gksudo gedit /boot/grub/menu.lst
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(gksudo:6379): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed


HELp

---

### Post by RomanIvanov on 2008-12-15
Did you tried simple "sudo gedit /boot/grub/menu.lst" ?

---

### Post by plucky on 2008-12-15
You are using Xubuntu so the normal install does not have **Gedit** as an editor.

Try ```
sudo nano /boot/grub/menu.lst
``` to edit the file and Ctrl <o> to write the file and Ctrl <x> to exit.


Good Luck

---

