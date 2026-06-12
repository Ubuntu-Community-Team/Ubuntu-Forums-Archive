---
title: "KDE icons not showing up properly in Gnome after intalling KDE plz Help!!!"
date: 2005-07-12
forum: Desktop Environments
---

### Post by braveerudite on 2005-07-12
](*,)   I am currently using Ubuntu and want to have KDE as well on my system.  The problem is that after installation.  KDE application ICONS (Some)  wont display on the Gnome menu. The KDE applications  are there and I can click on it and they would work. When I switch to KDE and access the menu, each option has their icon properly displaying next to their name.  What gives???  Everything else works fine...  It just that I hate to not  see them display properly when I'm using Gnome.  (makes my system look ugly)  Anyone else experiecing the same problem.  Please help me solve this.   ](*,)

---

### Post by trivialpackets on 2005-07-12
[QUOTE=braveerudite]](*,)   I am currently using Ubuntu and want to have KDE as well on my system.  The problem is that after installation.  KDE application ICONS (Some)  wont display on the Gnome menu. The KDE applications  are there and I can click on it and they would work. When I switch to KDE and access the menu, each option has their icon properly displaying next to their name.  What gives???  Everything else works fine...  It just that I hate to not  see them display properly when I'm using Gnome.  (makes my system look ugly)  Anyone else experiecing the same problem.  Please help me solve this.   ](*,)[/QUOTE]
 Uninstall KDE.  

All joking aside, you can use smeg menu editor to include the location for the kde icons, now you just have to find them.  This should resolve the issue.  Good luck.  apt-get install smeg I think works like a charm if I recall.

---

### Post by braveerudite on 2005-07-12
[QUOTE=eric.proctor]Uninstall KDE.  

All joking aside, you can use smeg menu editor to include the location for the kde icons, now you just have to find them.  This should resolve the issue.  Good luck.  apt-get install smeg I think works like a charm if I recall.[/QUOTE]

Few questions

1. Can you plz tell me were does KDE stores the ICONS?

2. What is the difference betweent??? 

computer:///    and   file:///     


The reason why I ask this is because when I download new wallpapers using the desktop control panel in KDE it gets store somewere call 

file:////home/jok3r/.kde/share/wallpapers/

But such folder I cant locate.

3. Where in Gnome can I go to configure the menu settings... this way I can set up the icns manually....

---

### Post by varunus on 2005-07-12
file:/// refers to the "Filesystem" icon in the Gnome computer.  The .kde folder has a '.' in front of it, so it will be hidden, but you can still access it.  In the fileselector dialog in gnome, you can hit / to bring up an "open location" dialog box.  Then type '/home/jok3r/.kde/share/wallpapers/' and hit enter.  Your wallpapers will be there.  KDE should store its icons in /usr/share/icons somewhere.

To configure the icons, you will need the SMEG menu editor.  [http://www.ubuntuguide.org](http://www.ubuntuguide.org) has instructions on how to set it up.  MAKE SURE you follow ALL of the instructions, make sure to enable extra repositories like it will tell you to, etc.

---

### Post by braveerudite on 2005-07-12
[QUOTE=varunus]file:/// refers to the "Filesystem" icon in the Gnome computer.  The .kde folder has a '.' in front of it, so it will be hidden, but you can still access it.  In the fileselector dialog in gnome, you can hit / to bring up an "open location" dialog box.  Then type '/home/jok3r/.kde/share/wallpapers/' and hit enter.  Your wallpapers will be there.  KDE should store its icons in /usr/share/icons somewhere.

To configure the icons, you will need the SMEG menu editor.  [http://www.ubuntuguide.org](http://www.ubuntuguide.org) has instructions on how to set it up.  MAKE SURE you follow ALL of the instructions, make sure to enable extra repositories like it will tell you to, etc.[/QUOTE]

Thank you for your time in answering .... I will work on that now and get back to you....  ](*,)

---

### Post by braveerudite on 2005-07-12
[QUOTE=varunus]file:/// refers to the "Filesystem" icon in the Gnome computer.  The .kde folder has a '.' in front of it, so it will be hidden, but you can still access it.  In the fileselector dialog in gnome, you can hit / to bring up an "open location" dialog box.  Then type '/home/jok3r/.kde/share/wallpapers/' and hit enter.  Your wallpapers will be there.  KDE should store its icons in /usr/share/icons somewhere.

To configure the icons, you will need the SMEG menu editor.  [http://www.ubuntuguide.org](http://www.ubuntuguide.org) has instructions on how to set it up.  MAKE SURE you follow ALL of the instructions, make sure to enable extra repositories like it will tell you to, etc.[/QUOTE]


Smeg is nowere to be found.... I try looking for it on synaptic and didn't find it either..... any clues??? ](*,)

Update: Nevermind I found it.    [http://amd64.ubuntuguide.org/#menu-editor](http://amd64.ubuntuguide.org/#menu-editor)

---

