---
title: "What is Plasma? and what is a plasmoid?"
date: 2009-03-21
forum: Desktop Environments
---

### Post by mahela007 on 2009-03-21
I just heard that Kubuntu 4.2 has been released. (yeah,, bit late). I would like to upgrade my existing version of KDE (4.1.x) to KDE 4.2
However it doesn't appear to be a straight forward procedure. I looked at the instructions on the KDE website but I don't really understand what they say..

"
**Instructions**

 The updated packages for Kubuntu 8.10 are in Unsupported Updates (backports). To update to KDE 4.2, please follow these instructions:
  
[LIST=1]
[*] Remove the koffice-data-kde4 package if you have it installed. The current koffice2 packages in the kubuntu-members-kde4 PPA are incompatible with the KDE 4.2 packages since they try to install icons to the same locations.
[*] Follow the [Kubuntu Repository Guide]("https://help.ubuntu.com/community/Repositories/Kubuntu") to enable *Recommended Updates* and *Unsupported Updates*.
[*] Old Plasma packages are not compatible with KDE 4.2, you should uninstall any plasmoids.
[*] You can now update any existing KDE 4 installation to 4.2 with Full Upgrade in the package manager, or using the Adept Updater tool in your system tray.
[*] Now log out. When you log in you will have KDE 4.2. Enjoy."
[/LIST]
First of all , what all this about removing a package?
What is "uninstalling plasmoids"?

---

### Post by SuperSonic4 on 2009-03-21
Plasma is the equivalent of the taskbar but it's also the desktop. Plasmoids are small apps that go on the system tray or the desktop to provide content

---

### Post by mahela007 on 2009-03-21
thanks for the quick reply
what do the instructions mean by saying "uninstall plasmoids"?

---

### Post by SuperSonic4 on 2009-03-21
It's asking you to remove the plasmoids/widgets you have in KDE 4.1 because they are not compatible with KDE 4.2, you should go into adept and remove the kdeplasma-addons package or similar although I upgraded from 4.1 to 4.2 without any problems

---

### Post by mahela007 on 2009-03-21
Does this also involve the default plasmoids? I haven't installed any new plasmoids. I only use the default ones

---

### Post by mahela007 on 2009-03-21
which one of these packages should I remove?
It might be hard to read them so here's a list
Kdebase-plasma
kdeplasma-addons
libplasma2
kdeplasma-addons-libs4
kdeplasma-addons-data

---

### Post by krazyd on 2009-03-22
Don't uninstall any of that. Plasmoids in the repositories are automatically upgraded to be compatible with KDE 4.2. 

Step three is simply if you have installed any 3rd party plasmoids manually (eg. from kde-look.org). It's not a big deal anyway, any plasmoids which aren't compatible will simply not load.

---

### Post by mahela007 on 2009-03-22
ah that clears up a lot. Thanks for your help.

---

