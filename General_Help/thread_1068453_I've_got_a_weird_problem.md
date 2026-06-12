---
title: "I've got a weird problem"
date: 2009-02-12
forum: General Help
---

### Post by commodore256 on 2009-02-12
I click on "Places" on the Gnome panel and then I click on "Home Folder" and blender opens. I've purged blender and I got this message.

"Error

Could not open location 'file:///home/myusername'
"blender" (No such file or directory)"

I dragged that launcher to the panel and I clicked on "Properties" and 
it said.

"Name: Home Folder
Location: file:///home/myusername
Comment: Open '/home/myusername'" (not important)

How do I reset that to open with Nautilus?

---

### Post by dcstar on 2009-02-12
> **commodore256 said:**
> I click on "Places" on the Gnome panel and then I click on "Home Folder" and blender opens. I've purged blender and I got this message.

"Error

Could not open location 'file:///home/myusername'
"blender" (No such file or directory)"

I dragged that launcher to the panel and I clicked on "Properties" and 
it said.

"Name: Home Folder
Location: file:///home/myusername
Comment: Open '/home/myusername'" (not important)

How do I reset that to open with Nautilus?

Have a look at this:

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

---

### Post by commodore256 on 2009-02-12
> **dcstar said:**
> Have a look at this:

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

That didn't do any thing.
the terminal said
"~/Desktop$ ./restorenautilus.sh 

You're missing a Computer .desktop backup file--nothing to restore


You're missing a Nautilus .desktop backup file--nothing to restore


You're missing a folder handler .desktop backup file--nothing to restore


You're missing a Home .desktop backup file--nothing to restore


You're missing a Network backup file--nothing to restore. If you had Thunar as your previous default file manager, this is normal.


Nautilus should now be your new default file manager in Gnome again"

Nautilus still works, it always had. When I click on my Home Folder shortcut on my desktop, it's fine, but the Home Folder icon in places on the Gnome panel _Still_ opens blender.

---

### Post by dcstar on 2009-02-12
> **commodore256 said:**
> That didn't do any thing.
the terminal said
..........
Nautilus still works, it always had. When I click on my Home Folder shortcut on my desktop, it's fine, but the Home Folder icon in places on the Gnome panel _Still_ opens blender.

I thought the script may have reset everything.

In Applications-System Tools-Configuration Editor have a look at the /desktop/gnome/volume_manager/filemanager key value ("nautilus -n --no-desktop %m" on mine)

Also have a look at the /desktop/gnome/applications/component_viewer/exec key (nautilus %s)

---

### Post by commodore256 on 2009-02-13
> **dcstar said:**
> I thought the script may have reset everything.

In Applications-System Tools-Configuration Editor have a look at the /desktop/gnome/volume_manager/filemanager key value ("nautilus -n --no-desktop %m" on mine)

Also have a look at the /desktop/gnome/applications/component_viewer/exec key (nautilus %s)

In Applications-System Tools the Configuration Editor isn't there.

There's only Cairo-dock, Compiz fusion icon, Virtual Box, Dolphin, dvdisaster, gISOMount, Gmount-iso, sysinfo and Winedoors inside System Tools there is no Configuration Editor.

PS: there is no Configuration Editor option in Edit Menus either.

---

### Post by zika on 2009-02-13
click on Alt-F2 (simultaneously) and enter "*gconf-editor*" in the panel You get.

(if that fails, "*sudo apt-get install gconf-editor*" (in Terminal) and then try again ...)

---

### Post by commodore256 on 2009-02-13
The terminal said the gconf-editor was already installed. (It's still not under system tools)

I put gconf-editor in the terminal and this was what I got.
[IMG]http://img150.imageshack.us/my.php?image=screenshotek6.png[/IMG]

As you can see, there is no volume_manager.

---

### Post by dcstar on 2009-02-13
> **commodore256 said:**
> The terminal said the gconf-editor was already installed. (It's still not under system tools)

I put gconf-editor in the terminal and this was what I got.
[IMG]http://img150.imageshack.us/my.php?image=screenshotek6.png[/IMG]

As you can see, there is no volume_manager.

Do a key search inside gconf-editor for the "Blender" command.

---

