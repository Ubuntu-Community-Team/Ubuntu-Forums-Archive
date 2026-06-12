---
title: "Bionic dock customisation"
date: 2019-04-22
forum: Desktop Environments
---

### Post by Newbunto on 2019-04-22
I've just upgraded from 16.04 LTS to 18.04 LTS (specifically 18.04.2).

With 16.04, on the left hand side of the screen was a bunch of icons (the dock?). I could *left* click on an icon and an application would be launched. I could *right* click on an icon and a menu would come up, from which I could select something. The way ***I*** had this set up was that the basic left click would launch the application with its default command line, while the right click would give me variations on the command line that would enable different options. For example, left click on the FileZilla icon would just launch FileZilla with default command line and hence default behaviour, while right click on the FileZilla icon and select something from the menu would allow me to launch FileZilla and, for example, automatically connect to the selected FTP site (hence multiple menu items in order to choose from among the available sites).

Is it still possible to do this on 18.04 ? If so, how?

At this stage I've worked out how to put my applications back on the dock but I don't get any useful right click menu. (For example, the FileZilla icon just offers me 'New Window', 'Remove from Favorites' and 'Show Details'.)

---

### Post by again? on 2019-04-22
Gnome/Ubuntu dock works with unity quicklist menus.
If you are creating your own quicklists you should copy the default desktop file from /usr/share/applications to ~/.local/share/applications.
Then edit the copied file.

eg my custom ~/.local/share/applications/nemo.desktop
```
[Desktop Entry]
Name=Nemo
Comment=Access and organize files
Exec=nemo --no-desktop %U
Icon=user-home
Terminal=false
Type=Application
StartupNotify=false
#OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Utility;Core;
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nemo
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=1.7.2
#NoDisplay=true

[COLOR="#FF0000"]Actions[/COLOR]=[COLOR="#800080"]Thunar[/COLOR];[COLOR="#FF8C00"]nautilus[/COLOR];[COLOR="#EE82EE"]recent[/COLOR];[COLOR="#006400"]Clear-recent[/COLOR];

[COLOR="#0000FF"][Desktop Action [COLOR="#800080"]Thunar[/COLOR]][/COLOR]
Name=Thunar
Exec=thunar
Icon=thunar

[Desktop Action [COLOR="#FF8C00"]nautilus[/COLOR]]
Name=Nautilus
Exec=nautilus
Icon=nautilus

[Desktop Action [COLOR="#EE82EE"]recent[/COLOR]]
Name=Recent
Exec=nemo recent:///
Icon=history

[Desktop Action [COLOR="#006400"]Clear-recent[/COLOR]]
Name=Clear Recent
Exec=/home/glen/scripts/clear-recent-confirm.sh
```

Check your file is using the correct syntax. Used to use "X-Ayatana-Desktop-Shortcuts" for [COLOR="#FF0000"]Actions[/COLOR] and the [COLOR="#0000FF"]group  headings[/COLOR] have also changed.
Old style example...
```
X-Ayatana-Desktop-Shortcuts=Screen;Window
 
[Screen Shortcut Group]
Name=Take a screenshot of the whole screen
Exec=gnome-screenshot
TargetEnvironment=Unity
 
[Window Shortcut Group]
Name=Take a screenshot of the current window
Exec=gnome-screenshot -w
TargetEnvironment=Unity
```

The gnome-shell dock does not show icons for quicklist menu items.
After any desktop file edits you may need to restart gnome-shell for the quicklist item to show in existing launcher.
Use alt+F2 to open the run dialog, type "r" and then hit Enter.

---

### Post by Newbunto on 2019-04-22
Thanks for the confirmation that it should work. Don't know why it all stopped working after the upgrade. I have reinstated the .desktop files and some of them now work.

The syntax must have changed earlier than 16.04 LTS because my .desktop files were already in the right syntax.

The one so far that is not working is [FONT=courier new]nautilus[/FONT]. I need to look into that some more and flail around some more.

The others started working immediately that I put the .desktop file in the right directory (no restart of any kind needed). The not working one is still not working even after a reboot.

Is there any kind of log file that might shed light on the processing of the various .desktop files on the dock? Where is the config for what's on the dock stored anyway? (I have things on the dock that I put there but which don't correspond to .desktop files and I have things on the dock that I don't think I even put there since the upgrade.)

---

### Post by again? on 2019-04-22
Post your nautilus .desktop file and I can test and have a look at, if you like.
You can try opening the .desktop in terminal with xdg-open to see if it reports errors.
eg.
```
xdg-open ~/.local/share/applications/gedit.desktop
```

There is also the command desktop-file-validate but I have never used.
Usage:
```
desktop-file-validate <path to desktop file>
```

---

### Post by Newbunto on 2019-04-23
> **guber2 said:**
> ```
xdg-open ~/.local/share/applications/nauti.desktop
```

No errors reported. Highlights the word "Utility" in red but that is in the original that I copied from /usr/share/applications in order to edit in my changes!

> **guber2 said:**
> ```
desktop-file-validate <path to desktop file>
```

That's happy. Gives one "hint" but otherwise all good.

[FONT=courier new]nauti.desktop: hint: value item "FileManager" in key "Categories" in group "Desktop Entry" can be extended with another category among the following categories: System;FileTools[/FONT]

Here's the .desktop file that I am using for testing.

```
[Desktop Entry]
# NotShowIn=Unity;GNOME;
Name=FilesTest
Comment=Access and organize files
# Translators: Search terms to find this application. Do NOT translate or localize the semicolons! The list MUST also end with a semicolon!
Keywords=folder;manager;explore;disk;filesystem;
Exec=nautilus --new-window %U
# Translators: Do NOT translate or transliterate this text (this is an icon file name)!
Icon=org.gnome.Nautilus
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Utility;Core;FileManager;
X-GNOME-UsesNotifications=true
Actions=new-window;tel;
X-Unity-IconBackgroundColor=#af4853
X-Ubuntu-Gettext-Domain=nautilus

X-AppStream-Ignore=true

[Desktop Action new-window]
Name=New Window
Exec=nautilus --new-window

[Desktop Action tel]
Name=tel
Exec=evince /tel.pdf
```

I have a feeling that 'Add to Favorites' is not adding what I think it is adding, which is why it would be good to know where the underlying config is stored. Equivalently, maybe I am not adding it correctly.

---

### Post by again? on 2019-04-23
Looking at 19.04 there doesn't appear to even be a **/usr/share/applications/nautilus.destop** file.
Installed desktop files by nautilus in 19.04...
```
**[COLOR="#006400"]glen@discotech:~$[/COLOR] dpkg -L nautilus | grep "\.desktop"**
/usr/share/applications/nautilus-autorun-software.desktop
/usr/share/applications/org.gnome.Nautilus.desktop
```
Installed desktop files by nautilus in 18.04...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] dpkg -L nautilus | grep "\.desktop"**
/etc/xdg/autostart/nautilus-autostart.desktop
/usr/share/applications/mount-archive.desktop
/usr/share/applications/nautilus-autorun-software.desktop
/usr/share/applications/nautilus-classic.desktop
/usr/share/applications/nautilus-folder-handler.desktop
/usr/share/applications/nautilus-home.desktop
/usr/share/applications/nautilus.desktop
/usr/share/applications/org.gnome.Nautilus.desktop
```


Try using the **org.gnome.Nautilus.desktop** file.
```
cp /usr/share/applications/org.gnome.Nautilus.desktop ~/.local/share/applications
```

Then edit for custom Actions....
```
gedit ~/.local/share/applications/org.gnome.Nautilus.desktop
```

I tested in 19.04 and 18.04 with this edited file to add nemo and both worked after restarting gnome-shell.
_**~/.local/share/applications/org.gnome.Nautilus.desktop**_
```
[Desktop Entry]
Name=Files
Comment=Access and organize files
# Translators: Search terms to find this application. Do NOT translate or localize the semicolons! The list MUST also end with a semicolon!
Keywords=folder;manager;explore;disk;filesystem;
Exec=nautilus --new-window %U
# Translators: Do NOT translate or transliterate this text (this is an icon file name)!
Icon=org.gnome.Nautilus
Terminal=false
Type=Application
DBusActivatable=true
StartupNotify=true
Categories=GNOME;GTK;Utility;Core;FileManager;
MimeType=inode/directory;application/x-7z-compressed;application/x-7z-compressed-tar;application/x-bzip;application/x-bzip-compressed-tar;application/x-compress;application/x-compressed-tar;application/x-cpio;application/x-gzip;application/x-lha;application/x-lzip;application/x-lzip-compressed-tar;application/x-lzma;application/x-lzma-compressed-tar;application/x-tar;application/x-tarz;application/x-xar;application/x-xz;application/x-xz-compressed-tar;application/zip;application/gzip;application/bzip2;
X-GNOME-UsesNotifications=true
Actions=new-window;[COLOR="#FF0000"]nemo[/COLOR]
X-Unity-IconBackgroundColor=#af4853
X-Ubuntu-Gettext-Domain=nautilus

OnlyShowIn=Unity;GNOME;

[Desktop Action new-window]
Name=New Window
Exec=nautilus --new-window

[COLOR="#FF0000"][Desktop Action nemo]
Name=Nemo
Exec=nemo
```[/COLOR]

---

### Post by Newbunto on 2019-04-24
Thanks for your help so far. Progress made!

The right-click menu now contains the expected additional actions. However ...

The actions don't work. Get spinning circle, which disappears after some time. Window never comes up.

---

### Post by again? on 2019-04-24
Yes i am also not able to launch evince from the dock quicklist but it does work from the plank dock.
I don't use gnome-shell or nautilus anymore and don't really know what Gnome is doing  in relation to Nautilus and the dock.
Might just be a bug. 

Easiest solution would be to create your own custom launcher with custom quicklists in ~/.local/share/applications
All you need as a base is something like below and add your own actions.
```
[Desktop Entry]
Name=Launchers
Exec=[COLOR="#696969"]<some command>[/COLOR]
Type=Application
Icon=[COLOR="#696969"]<path to an icon>[/COLOR]
Comment=My Launchers
StartupNotify=false

Actions=
```

eg this is my .desktop file I use for running often used commands and scripts
```
[Desktop Entry]
Name=Scripts
Exec=xdg-open /home/glen/scripts
Type=Application
Icon=/home/glen/Pictures/icons/coloured_folders/scripts-folder-flipped.png
Comment=My personal scripts
StartupNotify=false

# This sets the order of the Quicklist. Must match the [Desktop Action xxxxxxx]
Actions=Background;clock-seconds;game;network-restart;Ping;reloadPlank;Speed;swap;Test Script;RunTest;reloadtint2;Upper2lower;VivaldiCSS;VivaldiPatch;zsync;separator;edit-launcher;

[Desktop Action Background]
Name=Background Reset   
Exec=/home/glen/scripts/background-reset-gradient.sh

[Desktop Action Whatismyip]
Name=Whatismyip
Exec=/home/glen/scripts/whatismyip

[Desktop Action zsync]
Name=Zsync Daily Iso
Exec=xfce4-terminal --tab --drop-down --title "Zsync" -e "/home/glen/scripts/zsync.sh"

[Desktop Action Cursor]
Name=Change Cursor
Exec=xfce4-terminal --tab --drop-down -e "/home/glen/scripts/change-cursor-trusty"

[Desktop Action Test Script]
Name=Test Script Edit
Exec=gedit /home/glen/scripts/aatest.sh

[Desktop Action Screensaver]
Name=Screensaver  OFF/ON
Exec=/home/glen/scripts/toggle_screen_blanking.sh

[Desktop Action Equalizer]
Name=Equalizer
Exec=sh -c "pactl load-module  module-dbus-protocol; qpaeq"

[Desktop Action Notes]
Name=Notes
Exec=gedit "/media/Data/Notes"

[Desktop Action open-command]
Name=Open command in Terminal
Exec=/home/glen/scripts/xsel-terminal.sh

[Desktop Action RunTest]
Name=Test Script Run
Exec=gnome-terminal -e "/home/glen/scripts/aatest.sh"

[Desktop Action ClockToggle]
Name=Clock-Toggle
Exec=/home/glen/scripts/toggle-clock.sh


[Desktop Action TooltipToggle]
Name=Tooltip-Toggle
Exec=/home/glen/scripts/tooltips-toggle-trusty.sh

[Desktop Action Brightness]
Name=Brightness
Exec=/home/glen/scripts/brightness.py


[Desktop Action reloadtint2]
Name=Tint2 Reload
Exec=sh -c "killall tint2 && tint2 &"

[Desktop Action reloadPlank]
Name=Plank Reload
Exec=sh -c "killall plank && plank &"

[Desktop Action separator]
Name=______________________________________
Exec=

[Desktop Action edit-launcher]
Name=Edit Launcher
Exec=gedit /home/glen/.local/share/applications/MyScripts.desktop

[Desktop Action Ping]
Name=Ping Test
Exec=/home/glen/scripts/pingtest.sh

[Desktop Action Speed]
Name=Speed Test
Exec=/home/glen/scripts/speedtest.sh

[Desktop Action Upper2lower]
Name=Upper to Lower
Exec=/home/glen/scripts/upper2lower.sh

[Desktop Action getip]
Name=Get-IP Loop
Exec=sh -c "killall get-ip-loop.sh; sleep 2 && /home/glen/scripts/get-ip-loop.sh"

[Desktop Action game]
Name=Game Mode On/Off
Exec=/home/glen/scripts/game-settings.sh
Icon=/home/glen/Pictures/icons/bl2.png

[Desktop Action poker-fix]
Name=Poker Fix
Exec=xfce4-terminal --tab --drop-down -e "/home/glen/scripts/pokerth-sound-fix.sh"

[Desktop Action Buckle]
Name=Buckle On/Off
Exec=/home/glen/scripts/buckle-toggle.sh

[Desktop Action unilogout]
Name=Universal Logout
Exec=/home/glen/scripts/universal-logout.sh

[Desktop Action gnome-shell-replace]
Name=gnome-shell-replace   
Exec=/home/glen/scripts/gnome-shell-replace.sh

[Desktop Action network-restart]
Name=Network-restart   
Exec=xfce4-terminal --tab --drop-down --title "Network Restart" -e "/home/glen/scripts/network-restart.sh"

[Desktop Action swap]
Name=Swap Clear 
Exec=xfce4-terminal --tab --drop-down --title "Swap Toggle" -e "/home/glen/scripts/swap_toggle.sh"

[Desktop Action VivaldiPatch]
Name=VivaldiPatch   
Exec=xfce4-terminal --tab --drop-down --title "VivaldiPatch" -e "/home/glen/MEGAsync/configs/vivaldi/VivaldiPatch/vivaldi-patch.sh"

[Desktop Action VivaldiCSS]
Name=VivaldiCSS   
Exec=gedit /home/glen/MEGAsync/configs/vivaldi/VivaldiPatch/custom.css

[Desktop Action swaploop]
Name=Swap Loop 
Exec=xfce4-terminal --tab --drop-down --title "Swap Loop" -e "/home/glen/scripts/swaploop.sh"

[Desktop Action clock-seconds]
Name=Clock Toggle/seconds 
Exec=/home/glen/scripts/seconds-toggle.sh

[Desktop Action mydebs]
Name=Mydebs Repo Toggle 
Exec=xfce4-terminal --tab --drop-down --title "Mydebs Repo" -e "/home/glen/scripts/mydebs-repo-toggle.sh"

```

---

### Post by Newbunto on 2019-04-24
> **guber2 said:**
> 
Easiest solution would be to create your own custom launcher with custom quicklists in ~/.local/share/applications


OK, I've created the .desktop file.

How do I then get that .desktop file added to the dock? Just creating it in the right directory was not sufficient.

---

### Post by again? on 2019-04-24
> **Newbunto said:**
> OK, I've created the .desktop file.

How do I then get that .desktop file added to the dock? Just creating it in the right directory was not sufficient.
Should show in the Applications overlay where you can right click "Add to Favourites" or drag and drop on the dock.

---

### Post by Newbunto on 2019-04-25
> **guber2 said:**
> Should show in the Applications overlay where you can right click "Add to Favorites"

This only seems to work if you can *run the application* and that might depend on what the Exec command is in the .desktop file - and a lot of choices that I tried didn't seem to do what I want.

> **guber2 said:**
> or drag and drop on the dock.

That didn't work at all for me.

Anyway, I got it working - but in a ridiculous way. My .desktop file is files.desktop

so

```
sudo apt install gtk-3-examples
mkdir ~/bin
cp /usr/bin/gtk3-demo-application ~/bin/files
```

edit [FONT=courier new]files.desktop[/FONT] to [FONT=courier new]Exec=/home/<whatever>/bin/files[/FONT]

Then double click [FONT=courier new]files.desktop[/FONT] (that will launch some harmless example GUI application that will hang around i.e. needs to be long enough to do what I need to do)

Then I can 'Add to Favorites'

(Possibly it is then OK to delete ~/bin/files but I left it there in case I need to do further messing around.)

The only remaining problem is that I probably need to come up with a better Icon because I just grabbed a random .png file that was kicking around in my home directory tree. :)

Anyway thanks for your help and your patience.

---

### Post by again? on 2019-04-25
[LIST=1]
[/LIST]
In my tests a custom launcher will show even if the main exec line is empty
eg
```
Exec=
```

or just open a directory with xdg-open as in my previous example.
```
xdg-open /home/glen/scripts
```

**Note:** Desktop files don't do bash interpretation so use full paths to any scripts (don't use"~"). For **Exec=** you can use... 
[LIST]
[*]"<command> <options>"
[*]/full/path/to/script
[*]sh -c '[COLOR="#696969"]<some command> && <some other command>[/COLOR]'
[/LIST]
eg
[LIST]
[*]Exec=xdg-open /home/glen/scripts
[*]Exec=/home/glen/scripts/whatismyip
[*]Exec=sh -c 'notify-send "Starting get-ip-loop" && /home/glen/scripts/get-ip-loop.sh'
[/LIST]

 
If you have a command that includes special characters like "&&", put the command in a script and call the script or enclose in sh -c as above.
Make sure scripts are executable.

Search google images for pngs or somewhere like [https://www.iconfinder.com](https://www.iconfinder.com) for free svgs.
svg images scale better although some pngs are just as good for the dock.

---

### Post by Newbunto on 2019-04-25
> **guber2 said:**
> In my tests a custom launcher will show even if the main exec line is empty
```
xdg-open /home/glen/scripts
```

I don't want to mess with this again but I think what went wrong with this is that xdg-open of a directory launched nautilus and nautilus is already on the dock and so I didn't get the option to 'Add to Favorites'.

I did try "Exec=" and that produced an error I think but to be honest I didn't then test whether it was possible to add to favorites anyway.

> **guber2 said:**
> Search google images for pngs or somewhere like [https://www.iconfinder.com](https://www.iconfinder.com) for free svgs.
svg images scale better although some pngs are just as good for the dock.

Thanks for the suggestions.

As I don't need a real icon (it's not like I have to do i18n for *myself*), just one or more letters will do - hence I can make my own "logo" using GIMP or as a LibreOffice Drawing.

It is also possible to do a screen shot (window shot) to make the logo, although one needs to bear in mind that the result has a size of no more than 64 pixels.

---

### Post by mc4man on 2019-04-26
> **Newbunto said:**
> No errors reported. Highlights the word "Utility" in red but that is in the original that I copied from /usr/share/applications in order to edit in my changes!



That's happy. Gives one "hint" but otherwise all good.

[FONT=courier new]nauti.desktop: hint: value item "FileManager" in key "Categories" in group "Desktop Entry" can be extended with another category among the following categories: System;FileTools[/FONT]

Here's the .desktop file that I am using for testing.

```
[Desktop Entry]
# NotShowIn=Unity;GNOME;
Name=FilesTest
Comment=Access and organize files
# Translators: Search terms to find this application. Do NOT translate or localize the semicolons! The list MUST also end with a semicolon!
Keywords=folder;manager;explore;disk;filesystem;
Exec=nautilus --new-window %U
# Translators: Do NOT translate or transliterate this text (this is an icon file name)!
Icon=org.gnome.Nautilus
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Utility;Core;FileManager;
X-GNOME-UsesNotifications=true
Actions=new-window;tel;
X-Unity-IconBackgroundColor=#af4853
X-Ubuntu-Gettext-Domain=nautilus

X-AppStream-Ignore=true

[Desktop Action new-window]
Name=New Window
Exec=nautilus --new-window

[Desktop Action tel]
Name=tel
Exec=evince /tel.pdf
```

I have a feeling that 'Add to Favorites' is not adding what I think it is adding, which is why it would be good to know where the underlying config is stored. Equivalently, maybe I am not adding it correctly.

You should be able use the above .desktop pretty simply (I've no current gnome-shell session to ck..
Just create as is to ~/.local/share/applications,  you could name it as  nautilus.desktop if desired or as before.
Then as root delete /usr/share/applications/org.gnome.Nautilus.desktop  ( /usr/share/applications/nautilus.desktop can or not be also deleted, doesn't matter..

Use run command prompt  (alt+F2) to start your .desktop,i.e  
gtk-launch your .desktop name, ex. if its named nautilus.desktop  
```
gtk-launch nautilus
```
Pin icon & ck.

---

