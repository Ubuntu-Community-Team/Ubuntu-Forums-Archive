---
title: "Add an application"
date: 2014-04-13
forum: Desktop Environments
---

### Post by PM998 on 2014-04-13
Hi everyone,

I just upgrade to 14.04. So far so good. Now I would like to add a couple of script files to the "application" menu in order to have quicker access to these.
But I have not idea how to do this. In the old ubuntu (Gnome2), there are an edit menu option, but I cannot find this 14.04.

Any advice?

Thanks
  Peter

---

### Post by grumblebum2 on 2014-04-13
You would need to create a .desktop file in ~/.local/share/applications for each script.
May find it easier to create a .desktop file using a quicklist to run scripts you use frequently.

eg this is my **MyScripts.desktop** file.
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=
Name=MyScripts
Icon=/home/glen/Pictures/icons/Scripts Folder Badged.png

Actions=[COLOR="#FF0000"]altyo-fix[/COLOR];[COLOR="#40E0D0"]Change Cursor[/COLOR];[COLOR="#FF8C00"]Screensaver[/COLOR];[COLOR="#EE82EE"]Reset Wallpaper[/COLOR];

[Desktop Action [COLOR="#FF0000"]altyo-fix[/COLOR]]
Name=altyo-fix
Exec=/home/glen/scripts/altyo-fix.sh
TargetEnvironment=Unity

[Desktop Action [COLOR="#40E0D0"]Change Cursor[/COLOR]]
Name=Change Cursor
Exec=gnome-terminal -e '/home/glen/scripts/change_cursor'
TargetEnvironment=Unity

[Desktop Action [COLOR="#FF8C00"]Screensaver[/COLOR]]
Name=Screensaver ON/OFF
Exec=/home/glen/scripts/toggle_screen_blanking.sh
TargetEnvironment=Unity

[Desktop Action [COLOR="#EE82EE"]Reset Wallpaper[/COLOR]]
Name=Reset Wallpaper
Exec=/home/glen/scripts/background-reset.sh
TargetEnvironment=Unity
```

You can use this as a template and edit for your own needs.
In a terminal run... 
```
gedit ~/.local/share/applications/MyScripts.desktop
```
Copy and paste in the above .desktop file and edit for your use.

It's fairly simple.
The 
"Actions=[COLOR="#FF0000"]altyo-fix[/COLOR];Change Cursor;Screensaver;Reset Wallpaper;"
 line lists your actions which correspond to the name used in
[Desktop Action [COLOR="#FF0000"]altyo-fix[/COLOR]]
Name=altyo-fix          [COLOR="#800080"]# this can be whatever you like and is what is shown in the quicklist menu[/COLOR]
Exec=/home/glen/scripts/altyo-fix.sh  [COLOR="#800080"]# path to your script[/COLOR]      
TargetEnvironment=Unity

Once edited, save and drag and drop **~/.local/share/applications/MyScripts.desktop** to the launcher

---

### Post by grumblebum2 on 2014-04-13
....or if you can't be bothered with creating .desktops and quicklists you can use the **gnome-desktop-item-edit** command which
is available when you install gnome-panel.

In the terminal run....
```
sudo apt-get install --no-install-recommends gnome-panel
```

Then...
```
gnome-desktop-item-edit --create-new ~/.local/share/applications/ 
```

You will see the old create launcher dialog where you can create a launcher for your script 
which will be picked up by the dash.

---

### Post by deadflowr on 2014-04-13
You could install "alacarte", which is the name of what you know as main menu.
Which is what I think you want.

```
sudo apt-get install alacarte
```

---

### Post by PM998 on 2014-04-14
Thanks grumblebum2. This is exactly what I had in mind. Worked perfectly.

---

