---
title: "How can I disable the lock screen option for every user?"
date: 2014-11-27
forum: Desktop Environments
---

### Post by gad-maor on 2014-11-27
I have several machines running ubuntu 14.04 LTS and there are a lot of users that log in and out of them (not local users). I wish to prevent any possibility of a user locking the screen in a computer (thus leaving it unusable for other users). I tried to do it via gsettings, but it only applies to the gnome-session of the specific user from which the command was run.

Is there a way to do this with a script(sh) in the root directory, or by removing (uninstalling) the lock screen option completely from an ubuntu machine?

BTW, the display manager used is lightdm.

---

### Post by CantankRus on 2014-11-28
This should work to run the [COLOR="#FF0000"]dconf command[/COLOR] at every users login.
Create a global autostart file.
```
gksudo gedit /etc/xdg/autostart/disable-lock-screen.desktop
```
Copy and paste in the following...
```
[Desktop Entry]
Type=Application
Exec=[COLOR="#FF0000"]gsettings set org.gnome.desktop.lockdown disable-lock-screen true[/COLOR]
Hidden=false
**NoDisplay=true**
X-GNOME-Autostart-enabled=true
Name=LockScreen Disabled
Comment=Disable the lock screen
```

The **NoDisplay=true** line will make it not show up in each users startup applications.

---

### Post by CantankRus on 2014-11-28
Ok this is probably the right way to do it.
When Ubuntu used gconf you used to be able to set keys as mandatory.

Using [**_[COLOR="#B22222"]this guide[/COLOR]_**]("https://wiki.gnome.org/Projects/dconf/SystemAdministrators") I was able to disable-screenlocking for all users.

I've attached the files I created. You can use the included ReadMe.txt file to manually install
[SIZE=3]or[/SIZE]
Extract the archive and run the **install.sh** script in terminal to install the files.

The process can be reversed by running the **un-install.sh** script in terminal.

---

