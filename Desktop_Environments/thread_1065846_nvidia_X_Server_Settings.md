---
title: "nvidia X Server Settings"
date: 2009-02-10
forum: Desktop Environments
---

### Post by Sojurner on 2009-02-10
I have finally gotten my Dual monitors up and running (well the best i can at the moment).. Anyhow. I am unable to save my xconf.org file. It gives me an error about it not being able to make an xconf.org.backup.

How can i save this setting so i dont have to go back and resetup my dual monitors everytime i restart X or Restart my computer



2nd problem
I am also running Compiz and i have my windows set up with 3d Windows, Desktop Cube and the cylinder thing so its round instead of square. When i restart X or the PC i have to re enable all of these settings including the Visuals setting (when u right click on desktop and change background (the last tab) I have to reset all of this every time and its getting verry annoying. IF someone could please tell me how to get all these settings saved so that i dont ahve to do it i would greatly appreciate it

---

### Post by howefield on 2009-02-10
> **Sojurner said:**
> I have finally gotten my Dual monitors up and running (well the best i can at the moment).. Anyhow. I am unable to save my xconf.org file. It gives me an error about it not being able to make an xconf.org.backup.

How can i save this setting so i dont have to go back and resetup my dual monitors everytime i restart X or Restart my computer

If you are using an nvidia card and there is nothing customised in your xorg.conf, one possible solution would be to delete it after you log into X and then execute nvidia-settings.

```
sudo rm /etc/X11/xorg.conf
```

Then run nvidia-settings as root.

```
sudo nvidia-settings
```

Do your stuff, then when you go to save, you will need to specify the following folder to save to

```
/etc/X11/xorg.conf
```

---

### Post by SuperSonic4 on 2009-02-10
I'd still back up the original xorg.conf in the interests of safety:

```
sudo cp -v /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

The go into nvidia settings as root

```
gksu nvidia-settings
``` and do whatever you need to do and save then exit. Restarting X should solve your problem.

If it goes wrong drop into a console (ctrl+alt+f2) and do ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf
```

---

### Post by Sojurner on 2009-02-10
That has worked great as far as my multiple monitor set up goes. thanx guys..

However i am still having the issue of my Compiz settings not sticking when i restart X or the PC.I have to go back and resetup the desktop cube, 3dwindows and such. How can i make these settings stick just like the dual monitors so all ihave to do is log in and everything is the same?

---

### Post by Boaslad on 2009-03-07
I know that this reply is a little late in the game but I have a solution I came up with that might help some of you. It's simple but effective. I don't like using the terminal. (I know .. "boo.. hiss..." but to each their own.) So, Here's how I worked around the terminal for the nvidia-settings program.

1. Right click the menu and select "Edit Menus"
2. When the GUI comes up select "Administration" from the left column. (You may need to open "System" to find it)
3. In the right column find "NVIDIA X Server Settings" and right click it
4. Select "Properties"
5. Edit the "Command" line to read "gksu /usr/bin/nvidia-settings"
6. Close out and enjoy.

The Advantage of this? Now, I can just go to the Menu and select the program when I need it instead of opening the terminal. This trick can come in handy for a lot of other programs as well.

---

