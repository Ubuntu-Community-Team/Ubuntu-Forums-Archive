---
title: "Adding Rightclick context menu item for pictures"
date: 2012-04-26
forum: Desktop Environments
---

### Post by dzchimp on 2012-04-26
I'd like to add a Command "Upload to Server" as a right click item for pictures (extensions .jpg,.jpeg and .png), which would open a specific command "/userscripts/uploader path_and_name_of_picturefile"

Meaning I want to right click a file in Dolphin, choose the menu item "Upload to server", and my bash script should be invoked with an argument as the fullpath of file with the filename. My script would then take care of 'ftp put' for the file, then display the location where I have uploaded the file to.

The bash script is ready. I need to know how to add context menu items for specific file extensions, and pass the argument to my script, and then how to keep the "konsole" process active till I manually close it.

---

### Post by dzchimp on 2012-04-26
Ha.. I solved that one myself.

For Reference:
Create a new file in /usr/share/kde4/services titled uploadtoserver.desktop

Contents of this file:
```
[Desktop Entry]
Type=Service
ServiceTypes=KonqPopupMenu/Plugin
MimeType=image/*
Actions=uploader

[Desktop Action uploader]
Name=Upload Picture to Server
Icon=background
Exec=konsole --hold -e /dzbin/uploader %u
```

Contents of file /dzbin/uploader

```
#!/bin/bash
fullfile=$1
filename=$(basename $fullfile)
pathonly=${fullfile%/*} 
nameonly=${filename%.*}
fname=$(basename $fullfile)
ext=${fname##*.}
curdir=$(pwd)
#echo "Path of file is "$pathonly
#echo "Name alone is "$nameonly.$ext

if [ -d $pathonly ]
then
  cd $pathonly
fi
/home/droidzone/basic/uptest $nameonly.$ext
```

uptest is a compiled C program which interfaces with the ftp binary to upload the file to the server, retrieves the location and prints it to screen

A tutorial about service menus:
[http://techbase.kde.org/Development/Tutorials/Creating_Konqueror_Service_Menus](http://techbase.kde.org/Development/Tutorials/Creating_Konqueror_Service_Menus)

---

