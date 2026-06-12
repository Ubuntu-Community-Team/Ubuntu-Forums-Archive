---
title: "how do  add a 'Create Launcher to the GNOME 3 classic desktop"
date: 2012-07-03
forum: Desktop Environments
---

### Post by Philip Gray on 2012-07-03
Good evening

Does any one know how I can add a 'Create Launcher' option to the GNOME 3 Classic Desktop? I have found the following on the Linux Mint forum and a few other web sites however it does not work. The script they suggest shows in the Nautilus scripts folder but it does not run. However when I run the command in a terminal it works. The command is:
gnome-desktop-item-edit --create-new ~/Desktop

The suggestion was to create a script called 'Create Launcher' containing the above command and save it in:- ~/.gnome2/nautilus-scripts/ and then make it an executable file.

Regards
Philip

---

### Post by msammels on 2012-07-03
Hey Philip,

In order to help myself and the Ubuntu community best solve your problem, can you confirm what version of Ubuntu you are using? Is it still 10.04, or are you on 12.04 now?

If you are on either one, you will need to update to GNOME3 (10.04) or install GNOME3 (12.04) using the following command:

```
sudo apt-get install gnome-shell
```

However, I'm not sure that suggestion would work, because of the "gnome2" reference, but I could be wrong. In all honestly, it's easier to either open up another tty using the modifier keys like so:

```
CTRL+ALT+F1
```

And then starting LightDM (or GDM), and logging in there. Of course, you can log out of your current session and relog back into GNOME3. You can even set it as the default environment.

Oh and to get back to the default tty, the modifier is:

```
CTRL+ALT+F7
```

---

### Post by diesch on 2012-07-03
[Arronax]("http://www.florian-diesch.de/software/arronax/") gives you a "Create Launcher" option in the right click menu on the desktop and "Create launcher for this file" option in the right click menu of files.

Needs Ubuntu 12.04

---

### Post by dcsoldschool53 on 2012-07-03
In Ubuntu 12.04 download Ubuntu-Tweak. Inside Ubuntu-Tweak > Personal > Manage Scripts, you will see the nautilus-script folder. To the right of it, scroll down the list. Here you will find the script for create launcher, drag it to the left under the nautilus-script folder to add it to your right clicks.

This file is already executable.

---

### Post by Philip Gray on 2012-07-04
Hi Msammels

I am using both 10.04 and 12.04. I have 10.04 and Windows XP on my one drive which I dual boot using grub. 10.04 is the one that I am currently using. I purchased a third hard drive which I partitioned and installed 12.04 on. I did this to try out 12.04 and to see if I could get it to work like 10.04 for which support stops next year. I hate both the Unity and GNOME shell desktops so I have installed the GNOME Classic desktop.

This is one of the items that 10.04 has which is missing in 12.04. I want to iron out all the bugs and get the GNOME Classic to work like GNOME 2. I have noticed that a lot of the useful items in GNOME 2 are missing in GNOME 3. I have created a number of user accounts to test Cinnamon and KDE destops.

Regards
Philip

---

### Post by efflandt on 2012-07-04
I don't know default Gnome version used in 11.10 or 12.04, but In a terminal I used: ```
gnome-desktop-item-edit --create-new ~/Desktop
```to create a desktop launcher that I called "Make Launcher" containing:

```
sh -c 'gnome-desktop-item-edit --create-new ~/Desktop'
```The **sh -c** and single quotes are necessary so the launcher does not confuse or misinterpret parameters and shell expansion.

Note that if you want to make launchers for Unity bar;

[LIST]
[*]Install Main Menu (alacarte)
[*]Launch Main Menu from Dash and create a menu item (I forget if you have to logout, login for that to show up in Dash)
[*]Run the new item from Dash
[*]Right click its icon in Unity bar to select "Keep in launcher"
[/LIST]
I have used that to launch shell scripts in a terminal (for minecraft from Unity bar with icon extracted from minecraft.jar) or a Desktop launcher to launch minecraft server (gimp modified copy of minecraft icon with white S on it)

---

