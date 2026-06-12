---
title: "Uninstalling Azereus"
date: 2005-05-26
forum: Desktop Environments
---

### Post by YaAqoB on 2005-05-26
Hello.
I followed the guide at [www.ubuntuguide.org](www.ubuntuguide.org) and installed Arureus.
How do I uninstall it now that I don't want it there any more?

---

### Post by joele on 2005-05-26
Its good to get to know synaptic IMO...

So look in the system menu... Find 'Synaptic Package Manager' go into it, now up the top click search and put in the name of the program... It will filter the list.... simply right click the program and select remove.... you can then 'Apply' the changes...

You can also see in Synaptic all the programs available from the various apt sources (specified in your sources.list), most will have descriptions and you can add programs from here as well as remove (right click install)...

---

### Post by YaAqoB on 2005-05-26
Its in the list just its marked as uninstalled.
Thats what prompeted me to get rid of the old one and use the package manager to install it
Can I just delete it out of /opt and delete the .desktop from /usr/share/applications  ??

---

### Post by joele on 2005-05-27
Ahh sorry I didn't notice the install wasn't a deb file (just looked at  the guide) pretty silly to have that in the guide IMO... So yeah I guess you will just have to clean it out manually...

---

### Post by jeremy on 2005-05-27
[QUOTE=YaAqoB]Its in the list just its marked as uninstalled.
Thats what prompeted me to get rid of the old one and use the package manager to install it
Can I just delete it out of /opt and delete the .desktop from /usr/share/applications  ??[/QUOTE]
 Yes you can, you could also delete /home/YOUR_USER_NAME/.Azureus

---

### Post by joplass on 2005-05-27
[QUOTE=jeremy]Yes you can, you could also delete /home/YOUR_USER_NAME/.Azureus[/QUOTE]
My favorite! Get rid of the folder and you are home free.

---

