---
title: "Desktop Icons Moving in Xubuntu 14.04"
date: 2014-06-29
forum: Desktop Environments
---

### Post by lobonca2 on 2014-06-29
I have Xubuntu 14.04. I get the icons arranged just as I want them and often when I reboot they are all changed around. This is a pain and a waste of time. Is there a solution?

Thank you

---

### Post by ajgreeny on 2014-06-29
It has happened occasionally for a long time, right back to 12.04 which is the earliest Xubuntu I have used.

I am using xfce 4.10 on my precise install, and did not use 4.8 for any length of time, so I don't know if it's just a 4.10 problem.

I just keep a screenshot of the full desktop to make it much easier to put them all back in place if I need to, though mostly I start applications with an autohidden left side launchbar panel in my Xubuntu with all the same icons available there as well.

---

### Post by 2CV67 on 2014-08-15
> **lobonca2 said:**
> I have Xubuntu 14.04. I get the icons arranged just as I want them and often when I reboot they are all changed around. This is a pain and a waste of time. Is there a solution?

Since updating my Ubuntu with Xfce from 13.10 to 14.04 this week, I have exactly the same problem.

I have not seen any solutions proposed...

Thanks for any help!

---

### Post by garyzw on 2014-08-16
At certain events icons on the desktop rearrange themselves. This is because icon positions are determined by files in the ~/.config/xfce4/desktop/ directory. Each time a change is made to the desktop (icons are added or removed or change position) a new file is generated in this directory and these files can conflict.
To solve the problem, navigate to the directory and delete all the files.

---

### Post by rattskjelke on 2014-08-29
What certain events cause that?
I have been using Xubuntu 14.04 and my icons just started rearraging themselves in the past few days.
I deleted ~/.config/xfce4/desktop and let it rebuild whatever files were in there but that didn't help.
Is there a setting in some config file somewhere that toggles autoarrange?

---

### Post by go4unkwn2 on 2015-04-08
i solved this problem in xubuntu 14.04 with two bash scripts and two desktop files. the bash scripts i placed in /usr/local/bin and the desktop files in /usr/share/applications. the idea two solve the problem using bash i found in the net.

i use the bash scripts to backup and restore the icons.screen* file(s) in ~/.config/xfce4/desktop. the desktop file allows me a) to include into and run the bash scripts from the menu or panel. therefore i created some simple icons i use in the desktop files.

first bash script: backup icon file(s) after the icon on the desktop are grouped
```

#!/bin/bash
mkdir -p ~/.config/xfce4/desktop.bak
cp -f ~/.config/xfce4/desktop/icons* ~/.config/xfce4/desktop.bak

```

i named this script save-deskicon-pos.sh

second bash script: restore icon file(s) from the previously saved icon file(s)
```

#!/bin/bash
rm -rf ~/.config/xfce4/desktop
mkdir -p ~/.config/xfce4/desktop
cp -f ~/.config/xfce4/desktop.bak/icons* ~/.config/xfce4/desktop
xfdesktop --reload 2> /dev/null

```

i named this script load-deskicon-pos.sh

hint: you have to set the permissions for the bash script to chmod ugo+x

first desktop file: allows to run save-deskicon-pos.sh from menu or panel
```

[Desktop Entry]
Version=1.0
Type=Application
Exec=/usr/local/sbin/save-deskicon-pos.sh
Icon=desktopicons-save.png
Terminal=false
StartupNotify=true
Name=Fix Desktop Icons
Name[de]=Desktopicons fixieren
Comment=Save the last position of all desktop icons.
Comment[de]=Speichert die letzte Position der Desktopicons.
Categories=Utility;
OnlyShowIn=XFCE;

```

this desktop file i named desktopicons-save.desktop

second desktop file: allows to run load-deskicon-pos.sh from menu or panel (can also be used in autostart)
```

[Desktop Entry]
Version=1.0
Type=Application
Exec=/usr/local/sbin/load-deskicon-pos.sh
Icon=desktopicons-reload.png
Terminal=true
StartupNotify=true
Name=Replace Desktop Icons
Name[de]=Desktopicons neu ausrichten
Comment=Replace desktop icons to the old position.
Comment[de]=Verschiebt Desktopicons in die vorhgergehende Position.
Categories=Utility;
OnlyShowIn=XFCE;

```

this desktop file i named desktopicons-reload.desktop

hint: you have to create or download some icons and place them in /usr/share/icons/hicolor/YYxYY/apps (YY=36, 48, 64, 128, 256). i used gimp to scale the size of the icons. after i copied the icon into the apps folders i run

gtk-update-icon-cache /usr/share/icons/hicolor

the name of the icon files is the same in all different apps folders (see desktop files above).

in order to autostart the bash script, which restores the position of the desktop icons, at login, i created an autostart entry in "Einstellungen > Sitzung und Startverhalten > Automatisch gestartete Anwendungen".

hope this helps.

kind regards, go4unkwn

---

### Post by RangerK on 2015-05-01
Awesome!!!  Thank you, [**[COLOR=#000000]go4unkwn2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1933096")!

Here are a couple images I made for icons:
[http://i.imgur.com/RG7hBlf.png](http://i.imgur.com/RG7hBlf.png)
[http://i.imgur.com/91KypV0.png](http://i.imgur.com/91KypV0.png)

Also, after creating the scripts suggested above, I'd encourage other people to google "create desktop icon <your desktop environment>".  There are lots of shortcut ways to create desktop icons.

(On my Xfce box, creating the desktop files as described above didn't actually work.  While trouble shooting I discovered that I could simply right-click and "create-launcher".  Much easier.)

---

### Post by ajgreeny on 2015-05-03
One way to stop this happening is to make sure all your icons are where you want them to be on the desktop, then run command ```
sudo chattr +i /home/username/.config/xfce4/desktop/icons*
```which means the files are immutable and can not be changed in any way or deleted.

If you add another icon or file to the desktop after running this command, the icons may occasionally move around a bit, but can be put back in place by hitting F5 to refresh the desktop.

You can delete those icons* files if necessary by removing the immutable flag with ```
sudo chattr -i /home/username/.config/xfce4/desktop/icons*
```

---

### Post by pegasus-prodescargas on 2015-10-22
awsome @[COLOR=#000000]go4unkwn2 [/COLOR]! with the aswer's detail, i could deploy it on my xUbuntu 14.04

Thanks for all

---

### Post by gennarof on 2016-01-06
for people that are not familiar with scripts etc like me, I share this sort of ugly "solution"
you are basically doing manually what the  go4unkwn2 script above does automatically

go to the folder /home/"your user name"/.config/xfce4/desktop
it is an hidden folder, to make it visible press ctrl+H
once in the folder, create a link to the folder (in thunar you create the link in the menu "modify" of the top bar)
move the link folder to your desktop and maybe give it an easy to find name like DESKTOP or etc
before shutting down, click on the link folder "DESKTOP" , you will find  a text file on the style "icons.screen0-1424x884.rc" (or more than one  if you use the computer on more than one screen)
the file is the map of the icon position on your desktop
make a copy of the fine (copy and paste (ctrl+c and ctrl+v))
you have now a file called "copy of icons.screen0-1424x884.rc"
shut down
once you restart, if your icons have been bloody moved again, open the link folder "DESKTOP" you have created
open the "copy of icons.screen0-1424x884.rc"
select all ctrl+A   copy ctrl+C
open the map file "icons.screen0-1424x884.rc"
select all ctrl+A   copy ctrl+V
save it
close it
go to the desk top
press the button F5

it takes me 10 seconds, but still too long in our word, I know, but for handicapped like me...  could be useful and shorter than rearrange the icons manually each time
obviously, if you have not added/deleted/changed the position of the icons, you do not need to make a copy of the icon position map file
I am really surprised that they still have not fixed this error...

---

### Post by gorbeich on 2016-02-11
Hi,

I found this to work. The script just changes the attributes for the icon files to inmuttable for few seconds on startup to prevent them to be changed

Create this script:


```
#! /bin/sh
chattr +i ~/.config/xfce4/desktop/icons*
sleep 40
chattr -i ~/.config/xfce4/desktop/icons*


```

Give exec permissions, add the script to the sudoers and run it as root in autostart


Regards

---

