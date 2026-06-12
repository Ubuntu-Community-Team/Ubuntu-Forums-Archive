---
title: "gtk in Ubuntu?"
date: 2005-03-31
forum: Desktop Environments
---

### Post by delfin99 on 2005-03-31
Hi
I am trying to install thr GUI fot the gShield firewall. In the process it says that it need the GTK  but  cannot find. 
I want to know if GTK comes with Ubuntu. If not I would like to install it. Help needed.
TRhanks

---

### Post by jdodson on 2005-03-31
[QUOTE=delfin99]Hi
I am trying to install thr GUI fot the gShield firewall. In the process it says that it need the GTK  but  cannot find. 
I want to know if GTK comes with Ubuntu. If not I would like to install it. Help needed.
TRhanks[/QUOTE]

install as in source compile?  if you are compiling from source then you need to install the gtk development packages.  the synaptic program can help you do that.

---

### Post by arctic on 2005-03-31
do not forget that the devel-packages begin with lib and not with dev. a common mistake made by users. ;)

---

### Post by delfin99 on 2005-04-02
Hi again
I have installed libgtk2.0-dev, Then I do
root@ubuntu:/etc/firewaalGSgrafico/gshieldconf-0.40 # ./configure
 but i got the next message
[B]checking for gtk-config... no
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find GTK: Is gtk-config in path?[/B]

Do I need any more pakages, or is GTK installed in PREFIX (I dont know what exactly is this)?
Thanks

---

