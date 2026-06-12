---
title: "Weird GNOME error"
date: 2005-11-21
forum: Desktop Environments
---

### Post by Sverre Sundsdal on 2005-11-21
After a crash on my computer I can no longer log into gnome. After logging in in gdm nothing happens. I have reinstalled all vital gnome .debs but no success.
I installed kubuntu and tried to start gnome-terminal. 
I get the following error:Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE: 1.0
Adding client to server's list failed, CORBA error: IDL: omg.org/CORBA/COMM_FAILURE: 1.0

From the Konsole I find the following errors (I removed duplicates).
There was an error loading config from /apps/gnome-terminal/global. (Adding client to server
's list failed, CORBA error: IDL: omg.org/CORBA/COMM_FAILURE: 1.0 )
There was an error loading config from /apps/gnome-terminal/keybindings. (Adding client to s
erver's list failed, CORBA error: IDL: omg.org/CORBA/COMM_FAILURE:1.0 )
There was an error loading a terminal keybinding. (Adding client to server's list failed, CO
RBA error: IDL: omg.org/CORBA/COMM_FAILURE:1.0 )

There was an error loading config value for whether to use menu accelerators. (Adding client                                                               to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0 )
There was an error getting the list of terminal profiles. (Adding client to server's list fa                                                              iled, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0 )
There was an error loading config from /apps/gnome-terminal/profiles/Default. (Adding client                                                               to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0 )
There was an error loading config value for whether to use image in menus. (Adding client to                                                               server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0 )

(gnome-terminal:9995): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_ac                                                              cel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:9995): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_ac                                                              cel_group_from_accel_closure (accel_closure) != NULL' failed
There was an error loading config value for whether to use mnemonics. (Adding client to serv                                                              er's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
There was an error loading config from /desktop/gnome/interface. (Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:     1.0 )                                                                  


Any ideas ?

---

### Post by Orval on 2005-11-22
Hi Sverre,

I had a similar problem, see [this thread]("http://ubuntuforums.org/showthread.php?t=90102").

---

### Post by Sverre Sundsdal on 2005-11-22
The problem is not related to any of my  personal config files. I tried deleting all .gconf and .gnome dirs in my home directory. And I also tried to add a new user. 
My theory so far is that some important configuration file was damaged in the crash. If I could find out which one I could reinstall that .deb. If not I might have to reinstall the whole system.

---

### Post by VanHammersly on 2007-01-27
Hi.  For those who come here for future reference, I had the same problem and deleting ~/.gconfd/saved_state and (if it exists) ~/.gconfd/saved_state.tmp fixed the problem.

---

### Post by muzzamo on 2008-05-19
VanHammersly thanks for that. I got this problem on hardy and your suggestion fixed it.

---

### Post by m_bridge on 2008-06-12
Thanks, this fixed my edgy too, 
updating to the latest nvidia driver was the cause (173.14.05)

---

### Post by rodders on 2008-07-21
Hi,

Deleting ~/.gconfd/saved_state didn't work for me, but after doing it I also killed the process called "gconfd-2". The process restarted itself and the CORBA error stopped appearing.

Hope that helps.

---

