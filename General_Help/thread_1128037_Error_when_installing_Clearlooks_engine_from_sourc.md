---
title: "Error when installing Clearlooks engine from source"
date: 2009-04-17
forum: General Help
---

### Post by devosion on 2009-04-17
Due to unmet dependancies with cairo, pango, and atk, I was attempting to install gtk-2.0 from source. Everything seemed to have gone well. I managed to get past pango's cairo support problem, and got gtk-2.0 to install. But shortly after trying to configure clearlooks I receive the message telling me it isn't installed.

> 
./configure: line 22489: --variable=gtk_binary_version: command not found
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... configure: error: GTK+-2.0 is required to compile clearlooks-engine


Judging from my error lines either there is an option I need to set while running configure or I need to export an environment variable. Problem is im not sure what exactly it is I need to do to get configure to recognize the installed gtk-2.0. I verified the installation by checking the installation directory and gtk-2.0 installed correctly. What am I doing wrong and how can I fix this so I can install clearlooks and other gtk engines.

---

### Post by P4oL1n0 on 2009-04-17
Probably you should install libgtk2.0-0 package!

---

### Post by devosion on 2009-04-17
I just ran it through my aptitude just to be certain, and sure enough it acted like it was already installed. Also double checked my libraries and sure enough its where it should be. Any other ideas?

---

### Post by devosion on 2009-04-17
Stupid me. On a whim I checked to see if libgtk2.0-dev was installed. Sure enough it wasnt. I installed it and my configure went through.

---

### Post by P4oL1n0 on 2009-04-17
You won't believe it but i wanted to ask you that :D :D

---

