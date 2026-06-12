---
title: "Create launcher"
date: 2009-04-23
forum: General Help
---

### Post by noelc on 2009-04-23
Hi,

Can someone advise the best way to find the program (Command line) which needs to be entered when creating a launcher. I have download Virtual Box box and installed it but theres no icon so I need to create one. In windows it was just a matter of searching for  .exe files?

---

### Post by spiderbatdad on 2009-04-23
You dont need to install any software to create a launcher. Command line is your terminal prompt. Try this link. Someone's blog on creating launchers. It's really easy. You can do the same on the panel or desktop, depending where you right click.
[http://drbrainiac.wordpress.com/2007/11/04/how-to-create-custom-desktop-launchers-in-ubuntu-gnome/](http://drbrainiac.wordpress.com/2007/11/04/how-to-create-custom-desktop-launchers-in-ubuntu-gnome/)

---

### Post by noelc on 2009-04-23
> **spiderbatdad said:**
> You dont need to install any software to create a launcher. Command line is your terminal prompt. Try this link. Someone's blog on creating launchers. It's really easy. You can do the same on the panel or desktop, depending where you right click.
[http://drbrainiac.wordpress.com/2007/11/04/how-to-create-custom-desktop-launchers-in-ubuntu-gnome/](http://drbrainiac.wordpress.com/2007/11/04/how-to-create-custom-desktop-launchers-in-ubuntu-gnome/)

Ok Thanks but I don't know how to find the program I want to creat a launher for

---

### Post by djtnz on 2009-04-23
if you know the name of the executable, try

```
$ whereis nameofbinary
```

or otherwise you can try something like

```
$ sudo updatedb
$ locate virtualbox
```

---

### Post by aeiah on 2009-04-23
virtualbox menu item usually gets put in applications > system tools i think. if you havent got system tools visible then right click on the menu and edit it to enable the system tools submenu.

---

### Post by drs305 on 2009-04-23
aeiah is correct - it's in System Tools.

The actual executable location is found with:
```
which <appname>  # Example: which gimp
```
but you have to know the correct name to begin with.  For VirtualBox, the run command is "/usr/bin/VirtualBox" or "VirtualBox".

A way to find the program name is to type the first few letters in a terminal hit tab twice. It will display the available commands. In this case, typing "v" doesn't show any results for VirtualBox, but typing "V" and then double-tabbing produces "VBox" and "VirtualBox".

The icon is located at /usr/share/pixmaps/VBox.png

---

### Post by noelc on 2009-04-23
> **drs305 said:**
> aeiah is correct - it's in System Tools.

The actual executable location is found with:
```
which <appname>  # Example: which gimp
```
but you have to know the correct name to begin with.  For VirtualBox, the run command is "/usr/bin/VirtualBox" or "VirtualBox".

A way to find the program name is to type the first few letters in a terminal hit tab twice. It will display the available commands. In this case, typing "v" doesn't show any results for VirtualBox, but typing "V" and then double-tabbing produces "VBox" and "VirtualBox".

The icon is located at /usr/share/pixmaps/VBox.png

Thanks Guys when I type "" and double tab I got this.

VBox          VBoxManage    VBoxTunctl    VirtualBox    
VBoxHeadless  VBoxSDL       VBoxVRDP

Yes the icon was under the systems  menu but has disappeared? I,m trying to make a new one so I can execute Vbox

---

### Post by drs305 on 2009-04-23
> **noelc said:**
> Thanks Guys when I type "" and double tab I got this.

VBox          VBoxManage    VBoxTunctl    VirtualBox    
VBoxHeadless  VBoxSDL       VBoxVRDP

Yes the icon was under the systems  menu but has disappeared? I,m trying to make a new one so I can execute Vbox

To make a launcher, you don't *have* to have the icon, just the correct run command. The run command, at least for the non-OSE version, is "**VirtualBox**". Sometimes you have to specify the full path for the command, which for a normal install would be "**/usr/bin/VirtualBox**".

To find the icon, try running this:
```
sudo find /usr -type f -iname "VBox".png
sudo find / -type f -iname "VBox".png  # If not found with previous. This will take longer to run.
```

To add VirtualBox to your menu, if it isn't present in System Tools:
First, run one of the above commands to make sure it works (VirtualBox or /usr/bin/VirtualBox, then
```
alacarte  # opens the main menu for editing
```
Click on *System Tools* in the left pane.
In the right pane, if you are lucky, you will see an entry for VirtualBox. If so, just tick it so it displays when you select the *System Tools* menu.
If it isn't listed in the right panel, create a listing by clicking on "New Item" and entering the following:
Application
"VirtualBox"
"VirtualBox" (or whatever command you use. If "VirtualBox" doesn't work, use the full path, normally "/usr/bin/VirtualBox").
Double-click the icon symbol and enter the path you found to the icon, or browse to it.

---

