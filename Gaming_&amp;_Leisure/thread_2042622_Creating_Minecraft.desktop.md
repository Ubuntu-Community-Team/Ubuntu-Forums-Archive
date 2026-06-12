---
title: "Creating Minecraft.desktop"
date: 2012-08-15
forum: Gaming &amp; Leisure
---

### Post by Beardednerd on 2012-08-15
As of right now I have Java installed, and Minecraft works wonderfully if I start it via terminal. Now I'm attempting to create *.desktop file for it. Here is what I have so far;> #!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Icon[en_US]=gnome-panel-launcher
Name[en_US]=Minecraft
Exec=java -Xmx1024M -Xms1024M -cp ~/minecraft.jar net.minecraft.LauncherFrame
Name=Minecraft
Icon=gnome-panel-launcherHowever, this launcher will not launch like the ones I have created for other programs. The "java -Xmx1024M -Xms1024M -cp ~/minecraft.jar net.minecraft.LauncherFrame" command is the exact same one I use to launch Minecraft via terminal, so I'm 80% sure that isn't that problem. Which means I'm missing something elsewhere, and I can't see what - and it isn't as if [I did not look](http://www.nautilus-actions.org/?q=node/377).

Perhaps it's something I overlooked? Either way, I need a bit of help getting this working. Any ideas?

---

### Post by efflandt on 2012-08-16
I think you need to run minecraft from a terminal.  Simple way is to have the desktop call a script, which would be in your path if you put it in your ~/bin and have logged out of X at least once since you created that ~/bin.  I grabbed the icon from net/minecraft/favicon.png in the original minecraft.jar launcher.

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon[en_US]=gnome-panel-launcher
Name[en_US]=Minecraft
Exec=minecraft
Name=Minecraft
Icon=/home/efflandt/Pictures/Icons/minecraft.png
```The script is simply:

```
#!/bin/sh
# Change cd line to your path to orig minecraft.jar, NOT ~/.minecraft/bin
cd ~/MC-client
java -Xmx2G -Xms1G -cp minecraft.jar net.minecraft.LauncherFrame
```Note that the desktop launcher will not properly interpret multiple shell parameters, so for that, you need to single quote the string and run it in a shell.  I did some testing and this works (without adding the icon yet):

```
 
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon[en_US]=gnome-panel-launcher
Name[en_US]=Minecraft-direct
Exec=sh -c 'java -Xmx2G -Xms1G -cp ~/MC-client/minecraft.jar net.minecraft.LauncherFrame'
Name=Minecraft Directly
Icon=gnome-panel-launcher
```I do not know if the blank line at the top is important, but that is how it ended up when I originally used **gnome-desktop-item-edit --create-new ~/Desktop** from a terminal to create a desktop launcher to make desktop launchers:
```
 
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=gnome-panel-launcher
Name[en_US]=Make Launcher
Exec=sh -c 'gnome-desktop-item-edit --create-new ~/Desktop'
Name=Make Launcher
Icon=gnome-panel-launcher
```

---

