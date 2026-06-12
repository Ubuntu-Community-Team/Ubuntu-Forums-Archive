---
title: "Shortcut to .sh script on desktop (Ubuntu 14)"
date: 2015-11-16
forum: Desktop Environments
---

### Post by nathalie2 on 2015-11-16
I must have found almost 10 different ways to do this researching online, and none are working correctly.

I have an .sh script which launches a VPN client (gui).   From terminal I launch it as:
sudo ./fortisslvpn.sh

I'm trying to make a shortcut on the desktop. What I tried:



- creating a vpn.desktop file on the desktop, making it executable, setting "Files" to execute ([COLOR=#111111][FONT=Ubuntu]Files menu -> Edit -> Preferences -> behaviour tab [/FONT][/COLOR]):

[Desktop Entry]
Name=VPN
Exec=sudo ~/Downloads/forticlientsslvpn/fortisslvpn.sh
Terminal=true
Type=Application

(this opens a terminal asking for my root password, but then nothing happens)




- created a link by right-clicking my .sh script, and dragging that link to the desktop, making that shortcut executible.



- creating a file called vpn.sh on the desktop (making it executible) and with contents:
#! /bin/sh
sudo ~/Downloads/forticlientsslvpn/fortisslvpn.sh



- installing :
sudo apt-get install --no-install-recommends gnome-panel
then running:
gnome-desktop-item-edit ~/Desktop/ --create-new
and using that GUI to create my shortcut




None of these methods have worked. It shouldn't be this complicated I hope I'm just missing something stupid.

Thanks

---

### Post by mcduck on 2015-11-17
The first question would be if you are absolutely sure the program requires root permissions? That sounds unlikely to me. So the "sudo" part shouldn't be required. (Of course if the program was installed by extracting the files from a .zip or something and you ended running that command with sudo as well, the files would be owned by root and that could cause you to need sudo to execute them. In which case just change the ownership back to your own user, you should own all the files in your own home directory..)

...and then the actual solution for the .desktop file or link not working: maybe the program needs for you to be in the same directory with the executable when running it? Make sure you cd into correct direction first in your .sh script, or specify the path in the .desktop file. Also you should use the full path, the "~/" shortcut for your home directory is understood by CLI shells but won't work in .desktop files.

```
[Desktop Entry]
Name=VPN
Path=/home/yourusername/Downloads/forticlientsslvpn
Exec=fortisslvpn.sh
Terminal=true
Type=Application
```

```
#! /bin/sh
cd /home/yourusername/Downloads/forticlientsslvpn
./fortisslvpn.sh
```

If the program actually really needs root permissions, you can use pkexec (or gksudo) to get a graphical window asking for the password instead of having to open a terminal for it. Pkexec would be the preferred option, but requires a bit of configuration to get it working.

---

