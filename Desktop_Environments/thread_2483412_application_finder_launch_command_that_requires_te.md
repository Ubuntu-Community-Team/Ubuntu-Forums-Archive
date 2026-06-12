---
title: "application finder: launch command that requires terminal"
date: 2023-01-29
forum: Desktop Environments
---

### Post by Claus7 on 2023-01-29
Hello,

I tried to create a desktop shortcut to vmd and I wanted to launch vmd using xfce4-appfinder application. The shortcut under ~/.local/share/applications had the following options:
> [Desktop Entry]
Name=VMD 1.9.3
Exec=/usr/local/bin/vmd
StartupNotify=true
Terminal=true
Type=Application
Icon="path to the requested icon"

I could launch vmd everywhere apart from appfinder application: the application opened and then closed right away. If terminal was set to false, it couldn't be launched at all. So I had to modify the above like this:
> [Desktop Entry]
Name=VMD 1.9.3
Exec=gnome-terminal -e '/usr/local/bin/vmd'
StartupNotify=true
Terminal=false
Type=Application
Icon="path to the requested icon"

now it works from everywhere I want to launch vmd. Just check that now the option: terminal is set to false. Even though this means that no terminal will be used to open the requested application, that's remedied by issuing the gnome-terminal -e command above.

A similar command can be applied to vim as well:
```
gnome-terminal -e 'vim'

```
Regards!

---

### Post by Claus7 on 2023-01-29
Hello,

a related link for the above can be found here:
[https://askubuntu.com/questions/788736/open-vim-in-xfce4-terminal-from-thunar](https://askubuntu.com/questions/788736/open-vim-in-xfce4-terminal-from-thunar)

Also I want to add that I wanted to use right-click and open a file that vmd can open. I had done this before, yet now I used the following nautilus script added under: ~/.local/share/nautilus/scripts

> #!/bin/sh
filename=$1
gnome-terminal -e "/usr/local/bin/vmd $filename"

Mind the double quotes instead of using single ones, otherwise filename is not recognized.

Regards!

---

### Post by monkeybrain20122 on 2023-01-29
If you want to open any file 

then change the line in your bash script to

```
/usr/local/bin/vmd "$@"
```

Not sure if you need gnome-terminal -e

---

### Post by Claus7 on 2023-01-31
Hello,

> **monkeybrain20122 said:**
> If you want to open any file 

then change the line in your bash script to

```
/usr/local/bin/vmd "$@"
```

Not sure if you need gnome-terminal -e

thank you for your response. I tried your suggestion yet, what I was able to achieve is every time I open a terminal, vmd opens as well. I didn't see any new option while right clicking on a file. I added the line you propose under .bashrc.

Regards!

---

