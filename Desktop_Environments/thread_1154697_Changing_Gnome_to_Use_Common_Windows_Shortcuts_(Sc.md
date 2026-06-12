---
title: "Changing Gnome to Use Common Windows Shortcuts (Script)"
date: 2009-05-10
forum: Desktop Environments
---

### Post by Jebtrix on 2009-05-10
Just a uber simple bash script to change Gnome to common Windows shortcuts for those of us who just can't break the habit. The script also has a Restore function that will set everything back to Gnome defaults. 
[B]
Shortcut List: [/B]
Nautilus = **Win E**
Run Command = **Win R**
Search for Files = **Win F**
Show Desktop = **Win D **
**[COLOR="Red"]*[/COLOR]**System Monitor = **Control-Shift-F1**

***[COLOR="Red"]*[/COLOR]**Compiz prevents using the Escape key in command shortcuts so F1 is the closest button :(. If you don't use Compiz for your window manager then you can use Control-Shift-Escape as Windows does.*

You can either copy the code and save it to a file yourself or download the attached script file. 

```
#!/bin/bash
#Uses Shortcut Command Slots 10,11,12 to minimize the probability of
#overwriting any existing

echo ""
echo "Configure Gnome to use Windows common shortcuts"
echo "Shortcut List: Explorer, Run, Find, Show Desktop, Task Manager"
echo "   Press ( 1 ) to INSTALL"
echo "   Press ( 2 ) to RESTORE DEFAULTS"
read WORD
if [ $WORD = "1" ] ; then #INSTALL
 #File Manager
 gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_10 "nautilus computer:///"
 gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_10 "<Super>e"
 
 #File Search
 gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_11 "gnome-search-tool"
 gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_11 "<Super>f"
 
 #Show Desktop
 gconftool-2 -t str --set /apps/metacity/global_keybindings/show_desktop "<Super>d"
 
 #Run Command
 gconftool-2 -t str --set /apps/metacity/global_keybindings/panel_run_dialog "<Super>r"
 gconftool-2 -t str --set /apps/panel/global/run_key "<Super>r"
 gconftool-2 -t str --set /apps/compiz/plugins/gnomecompat/allscreens/options/run_key "<Super>r"
 gconftool-2 -t str --set /apps/compiz/plugins/ezoom/allscreens/options/fit_to_window_key "Disabled"
 
 #Task Manager/System Monitor
 #Note: Using <Shift><Control>Escape will not work with Compiz so F1 used instead
 #gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_12 "<Shift><Control>Escape" #Non-Compiz Window Manager (MetaCity,etc) 
 gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_12 "<Shift><Control>F1" #Compiz Version
 gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_12 "gnome-system-monitor"
 

 echo "Shortcuts Configured!"
 exit
elif [ $WORD = "2" ]; then #RESTORE
 #File Manager
 gconftool-2 --unset /apps/metacity/keybinding_commands/command_10
 gconftool-2 --unset /apps/metacity/global_keybindings/run_command_10
 
 #File Search
 gconftool-2 --unset /apps/metacity/keybinding_commands/command_11
 gconftool-2 --unset /apps/metacity/global_keybindings/run_command_11
 
 #Show Desktop
 gconftool-2 --unset /apps/metacity/global_keybindings/show_desktop
 
 #Run Command
 gconftool-2 --unset /apps/metacity/global_keybindings/panel_run_dialog
 gconftool-2 --unset /apps/panel/global/run_key
 gconftool-2 --unset /apps/compiz/plugins/gnomecompat/allscreens/options/run_key

 #Task Manager/System Monitor
 gconftool-2 --unset /apps/metacity/global_keybindings/run_command_12
 gconftool-2 --unset /apps/metacity/keybinding_commands/command_12

 echo "Shortcuts Restored!"
else
 clear
 echo "Invalid Selection"
 echo "Re-Run Script!"
fi
exit 0
```

To use: ```
sh configure.gnome.to.win.common.shortcuts.sh  
```

---

### Post by jpeddicord on 2009-05-12
Moved from Tutorials & Tips. Please see the [inclusion criteria]("http://ubuntuforums.org/showthread.php?t=677396"):

> The following items are not considered as tutorials.
    (...)
    * Posts that contain only downloadable scripts or debs. You are free to offer packages or scripts as part of your tutorial, but a script alone or a compiled package by itself does not constitute a tutorial. Threads like this will be moved to other areas.


---

### Post by nedkelly on 2009-05-13
I have a problem with shortcuts.

The shortcuts for "Run Command" and "Show Desktop" are working. But the other shortcuts are not.

When I go to the "compizconfig-settings-manager"-->"commands"-->"key bindings" the fields where the commands should be is blank, but when I click the fields, the command show??

What ever shortcut is configure in this way with "run command x" and "key bindings x" is not &#7811;orking.

Any idea to what is wrong

---

### Post by Jebtrix on 2009-05-13
I can confirm the part about compiz blank shortcut field until you click on it. It keeps showing blank everytime I relaunch  compiz manager until I actually go thru compiz's process of grabbing the key shortcut. Then the blank field shows properly.  As for the commands themselves being blank that is strange. I can't replicate that problem I'll look into it tonite.

You can manually check if the settings are getting entered by running:
```
gconf-editor
```
Search (CTRL + F) for command_10, run_command_10, etc. and you can confirm the entries are actually there. This is where compiz gets and sets the settings also.

If you disable compiz do the shortcuts work? What Ubuntu version you running? In Compiz Manager under Preferences do you have Backend set to GConf or Flat-File?

---

### Post by Jebtrix on 2009-05-13
I looked into this more and did direct comparisons of changes made manually thru Compiz Manager and ones by the script. The only discovery is these two lines can be commented out without adverse affects:

```
gconftool-2 --unset /apps/compiz/plugins/gnomecompat/allscreens/options/run_key
...
gconftool-2 -t str --set /apps/compiz/plugins/gnomecompat/allscreens/options/run_key "<Super>r"
```

I also found out even if you make all shortcuts manually thru Compiz Manager, Close it, Re-Launch it and immediately go into Commands > Key Bindings those shortcut fields are blank. If you hit Back, then return to Bindings they appear. ***OR*** if you launch Compiz Manager and just wait a few seconds then go into Commands > Key Bindings the fields show correctly. :???:

As for the blank Command Lines that one I cannot reproduce. :-k

---

