---
title: "trash can icon position on the desktop"
date: 2015-11-03
forum: Desktop Environments
---

### Post by drm200 on 2015-11-03
system: Ubuntu 14.04 64 bit with Nautilus

I'm trying to configure a unified desktop appearance on multiple machines.  I'm using gvfs-info and grep for nautilus-icon-position to get the desktop icon positions.  I can then use gvfs-set-attribute to place the icons where I want.  This method works well for all the icons that I have placed on the desktop.

However, gvfs-info does not return any information regarding the position of the Ubuntu "Trash", "Computer", "Home Folder", or  "Network Servers" icons .. So I do not know how to control the position of these four icons on the desktop.

Where is the position data for these 4 icons stored and is there a method to change the positional data?

---

### Post by ajgreeny on 2015-11-04
Why do you have desktop icons when you are using unity with the launchbar which already has a Trash icon at the bottom?  Are you using another DE and not unity?

---

### Post by drm200 on 2015-11-04
> **ajgreeny said:**
> Why do you have desktop icons when you are using unity with the launchbar which already has a Trash icon at the bottom?  Are you using another DE and not unity?


I am using Unity.  Using the desktop is my preference.  There are many reasons for that.  Hopefully, I can find some help here to identify how Ubuntu manages the position of the  "Trash", "Computer", "Home Folder", or "Network Servers" icons .


 

[COLOR=#000000][FONT=Ubuntubeta]



[/FONT][/COLOR]

---

### Post by brian-mccumber on 2015-11-04
Since it's only a few icons you are having problems with why not just manually place those where you want them?

---

### Post by ajgreeny on 2015-11-04
Are those 4 icons you are having the trouble with different from the usual **application.desktop** file launchers that are used as desktop icons?

I use xubuntu so can't really help more with this in unity, but I am aware that the 4 icons you speak of, if chosen to show on the xubuntu desktop, are not normal .desktop files and are not even visible in the Desktop folder in a file-manager window.  Perhaps that also is so in unity and gives you some food for thought. Perhaps you could replace the current icons with normal launcher .desktop files with content something like 
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Home
Comment=Browse the /home filesystem with the file manager
Exec=nautilus /home/*username*/
Icon=/usr/share/pixmaps/gnome-home.png # or your own choice.
Terminal=false
StartupNotify=false
Name[en_GB]=Home
Path=

```

---

### Post by yetimon_64 on 2015-11-04
> **ajgreeny said:**
> ... but I am aware that the 4 icons you speak of, if chosen to show on the xubuntu desktop, are not normal .desktop files and are not even visible in the Desktop folder in a file-manager window. ** Perhaps that also is so in unity** and gives you some food for thought. ...


That is right, they can be set or unset by altering "org.gnome.nautilus.desktop" settings in dconf editor in Unity. All 4 can be found there but don't have positional settings, just on or off etc. 

I agree trying new .desktop files for them  placed on the desktop may be a workable alternative here, though doing so most likely won't allow the bin full/empty icons to work as normal, but that is a pretty minimal hassle i.m.o.. Doing so should allow the position control as per all the other desktop icons. Cheers, yeti.

---

### Post by deadflowr on 2015-11-04
> **drm200 said:**
> I am using Unity.  Using the desktop is my preference.  There are many reasons for that.  Hopefully, I can find some help here to identify how Ubuntu manages the position of the  "Trash", "Computer", "Home Folder", or "Network Servers" icons .

Should be alphabetically.
Order will be home on top, then network , then trash, then volumes, and volumes will be alphabetical as well.

---

### Post by yetimon_64 on 2015-11-04
> **deadflowr said:**
> Should be alphabetically.
Order will be home on top, then network , then trash, then volumes, and volumes will be alphabetical as well.
...
> 
 I'm trying to configure a unified desktop** appearance on multiple machines**. I'm using** gvfs-info and grep for nautilus-icon-position** to get the  desktop icon positions.  I can then use** gvfs-set-attribute to place the  icons** where I want.

:-k ... @ OP, deadflower may be onto something here ... on all installs set the system icons by using dconf and they will show alphabetically (and be uniform across all desktops as such), then use your method for any others. If that works then you will at least retain the full system functionality of the trash icon etc. May be worth a shot.

---

### Post by drm200 on 2015-11-04
> **yetimon_64 said:**
> ...


:-k ... @ OP, deadflower may be onto something here ... on all installs set the system icons by using dconf and they will show alphabetically (and be uniform across all desktops as such), then use your method for any others. If that works then you will at least retain the full system functionality of the trash icon etc. May be worth a shot.

I'm trying to have a unified desktop on about 45 employee machines not all in the same physical location .. so i need to do this remotely.   Right now, I have a simple app that will position the icons uniformly .. except for the 4 icons.  And since I don't know the location of the icons, they can stack up.  

I had thought about new desktop files for the 4 .. but rejected it for loss of trashcan functionality .. 

I understand the dconf proposition but that is less than ideal .. I don't know the how to get the position/spacing for these four icons on all machines (which have different screens/resolutions) .. and as such don't know how to position & match spacing with the rest of the icons.  

The best solution for me would be to understand how to obtain/set the position of these four icons .. It must be stored somewhere.   It is very normal for companies to have uniform desktop environments ... this problem must have been solved before???

---

### Post by yetimon_64 on 2015-11-05
> The best solution for me would be to understand how to obtain/set the position of these four icons
I now have a much better idea of your needs with the last post of yours.

 I don't think it will be possible to obtain/set the position with the dconf settings. Just on or off as I understand the set up. 
If the .desktop idea is no good that leaves me at a loss at the moment. Hopefully someone else will think of an alternative than the 2 above. Good, luck. Yeti.

---

### Post by brian-mccumber on 2015-11-08
You can install Unity Tweak Tool from the software center and use it to turn those icons on and off. When you put those icons in position on your desktop they will stay in that position even after a reboot and also when turning them on and off from the tweak tool they still keep the same position on the desktop.

---

### Post by drm200 on 2015-11-12
> **brian-mccumber said:**
> You can install Unity Tweak Tool from the software center and use it to turn those icons on and off. When you put those icons in position on your desktop they will stay in that position even after a reboot and also when turning them on and off from the tweak tool they still keep the same position on the desktop.

The icons can be turned on/off from bash (no need for Tweak) ... but that does not solve my problem.

I need to be able to control the position of these icons programatically .   I can easily do this for all other desktop icons but these 4 icons are handled differently for some reason by Ubuntu.   I'm searching for how/where Ubuntu stores the position of these 4.   As mentioned in a previous post, I could turn the icons off .. and then create my own desktop icons for each ... but that solution doesn't work for the "trash" bin as it loses its visual aspect ... (and hence the focus on that icon in my original post) ... 


I'm still hoping someone can help me understand how/where Ubuntu stores the icon position information for the "trash"bin.

---

