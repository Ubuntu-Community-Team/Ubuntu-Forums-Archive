---
title: "Files responsible for holding desktop shortcuts"
date: 2010-06-28
forum: Desktop Environments
---

### Post by nkarkare on 2010-06-28
Hi
I use Ubuntu Netbook Remix (10.04) for my school labs (approx 200 clients), and wanted to remotely add or delete shortcuts on the desktop of a user. How do I do that? I found that .gtk-bookmarks has file related shortcuts, but what about the rest? As a last resort, I will have to use lsof and figure it out :-(
Thanks in advance,
Nikhil.

---

### Post by nothingspecial on 2010-06-28
They are in the ~/Desktop directory in the form of a script. They are called application.desktop and take this form
```

#!/usr/bin/env xdg-open

[Desktop Entry]
Name=Audacity
Name[de]=Audacity
Name[ru]=Audacity
GenericName=Sound Editor
GenericName[de]=Audio-Editor
GenericName[ru]=&#1056;&#1077;&#1076;&#1072;&#1082;&#1090;&#1086;&#1088; &#1079;&#1074;&#1091;&#1082;&#1086;&#1074;&#1099;&#1093; &#1092;&#1072;&#1081;&#1083;&#1086;&#1074;
Comment=Record and edit audio files
Comment[de]=Audio-Dateien aufnehmen und bearbeiten
Comment[ru]=&#1047;&#1072;&#1087;&#1080;&#1089;&#1100; &#1080; &#1088;&#1077;&#1076;&#1072;&#1082;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1077; &#1079;&#1074;&#1091;&#1082;&#1086;&#1074;&#1099;&#1093; &#1092;&#1072;&#1081;&#1083;&#1086;&#1074;

Icon=audacity

Type=Application
Categories=AudioVideo;Audio;AudioVideoEditing;

Exec=audacity
StartupNotify=false
Terminal=false
MimeType=application/ogg;audio/basic;audio/mpeg;audio/x-aiff;audio/x-mp3;audio/x-wav;application/x-audacity-project;
```

---

### Post by nkarkare on 2010-07-05
Figured it out. Just had to RTFM.
Here are the files needed to add shortcuts to desktops - in the Netbook Remix edition:
1. ~/.local/share/applications/ needs to have the .desktop files (I created mine with /usr/bin/alacarte so I had file names like alacarte-made-2.desktop)
2. ~/.config/menus/applications.menu is the file which has a reference to the desktop file.
Here is what mine looks like:
```
[INDENT]<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
        <Name>Applications</Name>
        <MergeFile type="parent">/etc/xdg/xdg-une/menus/applications.menu</MergeFile>
        <Menu>
                <Name>Education</Name>
                <Include>
                        <Filename>alacarte-made-2.desktop</Filename>
                </Include>
        </Menu>
</Menu>
[/INDENT]
```
Now, I can add whatever I want in this menu file and it will appear in that particular menu on the desktop.

---

