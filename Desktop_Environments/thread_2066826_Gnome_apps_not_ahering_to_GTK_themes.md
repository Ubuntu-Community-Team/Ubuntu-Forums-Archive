---
title: "Gnome apps not ahering to GTK themes"
date: 2012-10-05
forum: Desktop Environments
---

### Post by Kreuger on 2012-10-05
Hey guys, I've noticed that not all of my apps seem to adhere to using my GTK theme and I don't understand why. They have that old Windows 98 appearance to them. I've tried using themes like the gtk-theme-switch tool, lxappearance and gnome-control-center, now I'm at a loss. A couple of the apps are gksudo (when it pops up to ask for a password) and the odd thing about that is when it askes for the password for the manager (for example to enable wifi) that one comes up themed. But if I run a command from the terminal like gksudo synaptic, it's not themed. The other is actually related, gnome network manager. The menu from the system tray and the app itself are not themed. Gnome File Roller, the character map, disk utility (palimpsest), evince, simple-scan, gdebi, and the update manager are all others that don't work. Some of the ones that do are galculator, synaptic, exaile, gnumeric, pcmanfm, umplayer, tuxguitar.

---

### Post by vasa1 on 2012-10-05
> **Kreuger said:**
> Hey guys, I've noticed that not all of my apps seem to adhere to using my GTK theme and I don't understand why. ...
[LIST]
[*]Please provide the name of the theme. 
[*]Please provide the path to where your theme is located.
[*]Does it have gtk-2.0 and gtk-3.0 subfolders?
[*]Please provide your current OS. 
[*]Please provide your current DE.
[/LIST]
The business of the apps requiring gksudo has been answered. I'll search for the link and post here. It involves logical links.

---

### Post by vasa1 on 2012-10-05
See the posts here: [http://ubuntuforums.org/showthread.php?p=12187325](http://ubuntuforums.org/showthread.php?p=12187325)

Especially mcduck's post: [http://ubuntuforums.org/showpost.php?p=12182997&postcount=2](http://ubuntuforums.org/showpost.php?p=12182997&postcount=2)

---

### Post by Kreuger on 2012-10-05
The theme is called aurora-midnight. I have it in /usr/share/themes as well as in my own folder (/home/kreuger/.themes). Im not sure if it has both versions. Im running ubuntu 12.04 with Lxde. Im not concerned with why i need gksudo, the point is when the dialogue comes up asking for my password, its not themed, except when it comes up from the password manager.

---

### Post by Kreuger on 2012-10-19
Anyone?

---

### Post by TenPlus1 on 2012-10-19
Certain programs that run as root require themes need to be installed in the /usr/share/themes directory so that they work properly, it's a weird problem but can be fixed by typing these commands into Terminal and logging out and back in again:

 sudo ln -s ~/.themes /root/.themes
 sudo ln -s ~/.icons /root/.icons

---

### Post by vasa1 on 2012-10-19
> **Kreuger said:**
> The theme is called aurora-midnight. I have it in /usr/share/themes as well as in my own folder (/home/kreuger/.themes). Im not sure if it has both versions. Im running ubuntu 12.04 with Lxde. **Im not concerned with why i need gksudo**, the point is when the dialogue comes up asking for my password, its not themed, except when it comes up from the password manager.

Since OP isn't concerned, what can be said?

The other possibility maybe that OP is using "Lxde". I know that certain themes that work with Ubuntu (vanilla) or Xfce don't work well with pure Lubuntu. I don't know how they would work on a "hybrid" system.

---

### Post by Kreuger on 2012-10-26
> Certain programs that run as root require themes need to be installed in the /usr/share/themes directory so that they work properly, it's a weird problem but can be fixed by typing these commands into Terminal and logging out and back in again: I have it in there as well in the .themes folder in my home directory.


> **vasa1 said:**
> Since OP isn't concerned, what can be said?

The other possibility maybe that OP is using "Lxde". I know that certain themes that work with Ubuntu (vanilla) or Xfce don't work well with pure Lubuntu. I don't know how they would work on a "hybrid" system.

You completely misunderstood why I'm not concerned. I understand how it works and why.

---

### Post by ronniew on 2012-10-26
make sure your using a theme that supports, openbox, gtk2 and gtk3 since apps can be both gtk2 and gtk2

---

