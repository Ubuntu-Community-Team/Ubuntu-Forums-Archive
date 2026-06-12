---
title: "dbus no enviormental variable"
date: 2005-11-22
forum: Desktop Environments
---

### Post by gngulrajani on 2005-11-22
Hello All,

**update** 
i have found that the variable is set for the XSession  but not set for remotely logged in users. is this a bug?
***********
[I]
i was just experimenting with dbus and have found the default Ubuntu dbus init scripts:
/etc/init.d/dbus and /etc/X11/Xsession.d/75dbus-1-utils_dbus-launch

do not set the environmental variable DBUS_SESSION_BUS_ADDRESS. When this variable is not set some dbus tools fail to work such as:

$ dbus-monitor
Failed to open connection to session message bus: Unable to determine the address of the message bus
gregul@mighty:~/dev$ dbus-viewer
Could not open bus connection: Unable to determine the address of the message bus



is this a bug or a design decision?

-greg[/I]

---

### Post by perunaion on 2006-11-01
I am having a similiar error.  I noticed it because the Deleted Items folder wasn't showing.  And in the lower-right corner is an error message saying:
```
Failed to connect to the Deleted Items  Folder: Unable to determine the address of the message bus
```
Anyone have an suggestions on the matter?

---

### Post by sloggerkhan on 2006-11-05
I've just been working on an update from dapper to edgy and the files you mentioned don't exist on my machine and I keep getting dbus error.

---

### Post by sloggerkhan on 2006-11-05
> **sloggerkhan said:**
> I've just been working on an update from dapper to edgy and the files you mentioned don't exist on my machine and I keep getting dbus error.

I used aptitude to fix things a lot (more or less automatically) and eventually my system got working.

---

### Post by aguy on 2006-11-05
Is this the reason that when I log into Edgy from my windows machine runnning (which runs Xming xserver and putty SSH) that the default gnome theme doesn't work?  There were no problems like this when I was running breezy, but now there is an error about dbus when I log in remotely as stated above.

Regards

---

