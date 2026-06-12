---
title: "gnome-panel dont work"
date: 2009-08-07
forum: Desktop Environments
---

### Post by ulissess on 2009-08-07
hi guy, i just have removed and reinstalled gnome-panel, gnome-applets and gnome-applets-data  but i have always same errors.. this is my output.


> root@valerio-laptop:/home/valerio# gnome-panel

(gnome-panel:6428): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.

** (gnome-panel:6428): WARNING **: Error getting value of '/apps/panel/global/locked_down': Contatto col server di configurazione fallito; tra le possibili cause la necessità di abilitare il supporto a TCP/IP per ORBit o la presenza di un vecchio lock NFS a causa di un crash di sistema. Consultare [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) per ulteriori informazioni (Dettagli -  1: Recupero delle connessione alla sessione fallito: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)


** (gnome-panel:6428): WARNING **: Error getting value of '/desktop/gnome/lockdown/disable_command_line': Contatto col server di configurazione fallito; tra le possibili cause la necessità di abilitare il supporto a TCP/IP per ORBit o la presenza di un vecchio lock NFS a causa di un crash di sistema. Consultare [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) per ulteriori informazioni (Dettagli -  1: Recupero delle connessione alla sessione fallito: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)


** (gnome-panel:6428): WARNING **: Error getting value of '/apps/panel/global/disable_lock_screen': Contatto col server di configurazione fallito; tra le possibili cause la necessità di abilitare il supporto a TCP/IP per ORBit o la presenza di un vecchio lock NFS a causa di un crash di sistema. Consultare [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) per ulteriori informazioni (Dettagli -  1: Recupero delle connessione alla sessione fallito: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)


** (gnome-panel:6428): WARNING **: Error getting value of '/apps/panel/global/disable_log_out': Contatto col server di configurazione fallito; tra le possibili cause la necessità di abilitare il supporto a TCP/IP per ORBit o la presenza di un vecchio lock NFS a causa di un crash di sistema. Consultare [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) per ulteriori informazioni (Dettagli -  1: Recupero delle connessione alla sessione fallito: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)


** (gnome-panel:6428): WARNING **: Error getting value of '/apps/panel/global/disable_force_quit': Contatto col server di configurazione fallito; tra le possibili cause la necessità di abilitare il supporto a TCP/IP per ORBit o la presenza di un vecchio lock NFS a causa di un crash di sistema. Consultare [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) per ulteriori informazioni (Dettagli -  1: Recupero delle connessione alla sessione fallito: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)


** (gnome-panel:6428): WARNING **: Failed to load default panel configuration. panel-default-setup.entries hasn't been installed using gconftool-2 --load ?


thank u...

---

### Post by asmoore82 on 2009-08-07
You should not be running it as root

---

### Post by ubudog on 2009-08-08
No you shouldn't.  It will probably work if you just open a terminal without root and then try.  Hope that helps! :P

---

### Post by carlodrengen on 2009-08-08
i cant see the programs i haw open on my desktop on my bottom bar 
and i hawent made any change's to it when i install ubuntu it was there
now it is not dunno why

---

### Post by ubudog on 2009-08-08
Just open a regular terminal,no root, and type gnome-panel.  Then it should work.  Hope that helps!  :P

---

### Post by gjoellee on 2009-08-08
(as said before) don't run gnome-panel as root user.

---

### Post by ulissess on 2009-08-08
oh yeah !! now it's ok!! many thanks!!!

---

### Post by ubudog on 2009-08-08
> **ulissess said:**
> oh yeah !! now it's ok!! many thanks!!!

Many welcomes. :P

---

