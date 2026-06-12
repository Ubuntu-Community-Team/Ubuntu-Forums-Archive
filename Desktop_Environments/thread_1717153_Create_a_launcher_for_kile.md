---
title: "Create a launcher for kile"
date: 2011-03-29
forum: Desktop Environments
---

### Post by masodin on 2011-03-29
hi there,

i just compiled kile-2.1b5. When typing 

KDEDIRS=$HOME/kile/kile-install:$KDEDIRS $HOME/kile/kile-install/bin/kile

in the terminal kile pops up which is great.

Nevertheless, i wish to create a launcher for kile in the panel.

I have found this thread

[http://askubuntu.com/questions/17361/create-a-launcher-for-kile-built-from-source](http://askubuntu.com/questions/17361/create-a-launcher-for-kile-built-from-source)

My desktop configuration file looks like this:

[Desktop Entry]
Name=Kile
GenericName=LaTeX Editor
Comment=Edit Texfiles
Exec=sh -c "KDEDIRS=$HOME/kile/kile-install:$KDEDIRS $HOME/kile/kile-install/bin/kile"
Terminal=false
Type=Application
Icon=$HOME/kile/kile-install/share/icons/hicolor/128x128/apps
Categories=Office

After having made it executable and doubleclick, the splashscreen of kile pops up followed by a  small window named "Kile-The KDE Crash Handler" saying "Executable: kile PID: 10341 Signal: 11 (Segmentation fault)"

Same happens with kile-2.1b4 (which was already running on my system [Ubuntu 10.10] before)

Any ideas?

Thanks,

masodin

---

### Post by nickleboyblue on 2011-03-29
Right-click the panel you want to put a launcher up for.  In the context menu, click on the entry for "Add to Panel...".  This will bring up a dialog that is normally used to add stock widgets to the panel, but you can also add custom application launchers.  At the very top of that dialog, you click on the button labeled "Custom Application Launcher" and a new window will pop up.  In this window, you can change the icon for your application, enter the application's name, and enter the command you type in the terminal to get the application to run.  If your program requires root access, there are a few extra things you need to do, but I'm not THAT much of an expert yet.

So, as far as desktop configuration files, etc., you don't even need to look at them.  Just do it through the GUI, and everything will be taken care of for you, except for the icon.  You will have to manually locate the icon and set it in the launcher editor window.

As for the segmentation fault, I don't know what would cause that.  Does it do that when you run it straight from the command line?

---

### Post by masodin on 2011-03-29
hi nickleboyblue,

i should have mentioned that I already created a launcher as suggested by yourself as well. Unfortunately, this generates the same result. However, if I type

KDEDIRS=$HOME/kile/kile-install:$KDEDIRS $HOME/kile/kile-install/bin/kile

in the terminal kile starts as expected. I really do not know where the problem is. All the folders necessary to compile kile have been placed in $HOME. There are also no padlocks on the folder icons suggesting a rights issue. But i am still a noob, so i hope that some expert out there will help.

masodin

---

### Post by masodin on 2011-03-29
hi all,

i just had to get rid of some padlocks on the folders .kde, .qt, .lyx.
Now, everything is fine.

Sorry for that, but i am still a noob, a lucky noob now :P

---

