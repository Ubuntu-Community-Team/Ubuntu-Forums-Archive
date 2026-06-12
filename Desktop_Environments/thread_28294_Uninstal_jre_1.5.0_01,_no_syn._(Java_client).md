---
title: "Uninstal jre 1.5.0_01, no syn.? (Java client)"
date: 2005-04-19
forum: Desktop Environments
---

### Post by coldturkey on 2005-04-19
I just did the stupidest thing ever... Installed jre-1_5_0_01-linux-i586 on the desktop because it never asked for a location!... However I wanna uninstall this sh*t but don't know howto, I've looked in Synaptics, nothing there....

Any help :/ Or am I doomed with this document on my desktop? Btw, I don't have any rights to this folder, I "don't own it".... Wierd :/

---

### Post by Leif on 2005-04-19
If you installed it using sun's installer, it won't be in synaptic. Have you tried deleting it using sudo ?

---

### Post by coldturkey on 2005-04-19
[QUOTE=Leif]If you installed it using sun's installer, it won't be in synaptic. Have you tried deleting it using sudo ?[/QUOTE]

Sorry, don't know how to do that. I've tried sudo uninstall, sudo remove, sudo dpkg -i, all tries - I don't know howto delete :/.... :)

---

### Post by gunnyman on 2005-04-19
open a terminal window
type sudo nautilus
navigate to home/yourusername/Desktop
use cut on the  java folder
navigate back to /usr/lib
paste folder there.
redo symlinks if needed to get the firefox plugin working 
change your JAVA_HOME environment (if one was set) to reflect the new location.

---

