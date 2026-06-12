---
title: "Working Directory of Service Menus"
date: 2012-08-23
forum: Desktop Environments
---

### Post by tristicles on 2012-08-23
Hi all. Have been a Gnome user since starting with Ubuntu back in the Feisty days. Have flirted with KDE here and there but never really given it a good enough crack of the whip. I'm afraid I'm not really keen on Unity. Gnome Shell requires too much effort to get it useable. XFCE isn't too bad, but it's a bit rough round the edges. It's time to give KDE another go.

My sticking point is Service Menus and the working directory. I've written an really simple script to rename files in preparation for publishing on the web.

```
#!/bin/bash
for arg
do
  converted_name=$(echo "$arg" | sed -e 's/ /-/g' | sed -e 's/_/-/g' | tr [A-Z] [a-z])
  mv "$arg" "$converted_name"
done
```

It lower-cases everything and replaces spaces and underscores with a dash. IE "File_name with space.txt"  would become "file-name-with-space.txt". It works perfectly in Gnome with Nautilus Scripts. KDE, however, is making me work!!!

I've made a service menu for it... 

```
[Desktop Entry]
Type=Service
ServiceTypes=KonqPopupMenu/Plugin
MimeType=application/octet-stream
Actions=renameForWeb

[Desktop Action renameForWeb]
Name=Rename For Web
Exec=/home/me/scripts/rename-files.sh %U
```

...but it's not quite working properly. The "%U" on the exec line passes in the full path for each file. That's nice and comprehensive. However, my script won't work properly with that.

For example, "/home/me/Pictures/File Name.jpg" will get converted to "/home/me/pictures/file-name.jpg". The "pictures" folder will also get lower-cased, causing the script to fail.

The other option is to use %N on the exec line which passes in just the file names, without the path. The problem with that, is that the working directory isn't where the files you've selected are (ie the ~/Pictures folder in this example). It seems to be using ~/scripts as the working directory.

I realise I could try and pass the working directory from the service menu to the script but that will mean re-writing the script and making it pretty complicated. Is there any way of changing the working directory in the service menu, before executing the script?

This is my "got to have" thing. If I can get this working, you've got a KDE convert on your hands!!

---

### Post by tristicles on 2012-08-24
Help me Obi-Wan Kubuntu. You're my only hope

---

### Post by tristicles on 2012-08-28
OK, I've given up and started over. The exec line now uses %F

```
[Desktop Entry]
Type=Service
ServiceTypes=KonqPopupMenu/Plugin
MimeType=application/octet-stream
Actions=rename_for_web

[Desktop Action rename_for_web]
Name=Rename for Web
Exec=~/scripts/kde-rename-files.sh %F
```

The kde-rename-files script splits the full-path file name into folder and filename and processes accordingly
```

#!/bin/bash

for file in "${@}"
do
  dir=$(dirname "$file")
  cd "$dir"
  filename=$(basename "$file")
  new_name=$(echo "$filename" | sed -e 's/ /-/g' | sed -e 's/_/-/g' | tr [A-Z] [a-z])
  mv "$file" "$new_name"
done
```

Hope this comes in useful for someone.

---

