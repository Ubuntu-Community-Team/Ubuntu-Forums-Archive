---
title: "Invisible black hole where icons disappear when dropped"
date: 2014-08-24
forum: Desktop Environments
---

### Post by fly-by-night on 2014-08-24
I did something like ctrl+drag the Home icon. It started copying and I immediately cancelled. The Home icon is on the new position, but the old location is now the black hole (selected area next to Home icon). Hidden files (none) is shown in file browser from screenshot below.

Screenshot:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=255787&d=1408870888[/IMG]

When I drag any icon (not Home) there, it disappear. If I drag Home to the black hole, it starts copying something:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=255786&d=1408870838[/IMG]

It only happen on this black hole (selected area on 1st screenshot). This is the icon location as per /home/extraa/.config/xfce4/desktop/ :
```
[xfdesktop-version-4.10.3+-rcfile_format]
4.10.3+=true

[/home/extraa/Desktop/gimp.desktop]
row=2
col=0

[/home/extraa/Desktop/gcalctool.desktop]
row=4
col=0

[/home/extraa/Desktop/vlc.desktop]
row=3
col=0

[/home/extraa/Desktop/simple-scan.desktop]
row=0
col=0

[/home/extraa/Desktop/Chromium 38.0.2109.0]
row=5
col=0

[/home/extraa/Desktop/firefox.desktop]
row=1
col=0

[/home/extraa/Desktop/libreoffice-writer.desktop]
row=3
col=1

[/home/extraa]
row=0
col=1


```

---

### Post by ajgreeny on 2014-08-24
If you have the Desktop preferences set to show filesystem, home and trash icons on the desktop, I think you will find that they are not "icons" as such, like other desktop icons for applications, but are more like soft-links to the appropriate folders, and therefore perhaps if you try to copy them all the files in those folders will be copied, not just the icons.

If you look in thunar at the Desktop folder you will notice that the filesystem, home and trash icons do not show, only the icons that are .desktop, such as your vlc.desktop, files will show as files.

---

### Post by fly-by-night on 2014-08-24
> **ajgreeny said:**
> If you have the Desktop preferences set to show filesystem, home and trash icons on the desktop, I think you will find that they are not "icons" as such, like other desktop icons for applications, but are more like soft-links to the appropriate folders, and therefore perhaps if you try to copy them all the files in those folders will be copied, not just the icons.

If you look in thunar at the Desktop folder you will notice that the filesystem, home and trash icons do not show, only the icons that are .desktop, such as your vlc.desktop, files will show as files.
I did not even notice that the Home etc icons do not show in the Desktop folder, thank you. 

I dropped another icon on the black hole and decided to go look for the missing icons/shortcuts. They are all in the home folder. I think the icon (and somehow the clickable link) is missing, yet the Home (copy) is active on the desktop. That explain the icons being moved to the home folder from Desktop and the copy process that start when dropping Home icon there.

edit: The selected area on my first screenshot was done by dragging the mouse. There is literally nothing there

---

