---
title: "configure .desktop file to use console mplayer (space and non-latin char problem)"
date: 2012-09-15
forum: Desktop Environments
---

### Post by buzlite on 2012-09-15
I'm running lubuntu 12.04.1 64bit.

I'm trying to configure my system to launch audio/video files using the console mplayer.

The problem is that after I've configured the .desktop file to launch the console mplayer, filenames containing non-latin characters and/or spaces do not work.  Mplayer works with these filenames when I run it in lxterminal by manually entering these filenames.

Here's what I've done.

I created console-mplayer.desktop.  The relevant content in this file is shown below.


```

[Desktop Entry]                
Version=1.0
Name=consolemplayer
...
Exec=lxterminal --geometry=80x5 -t "mplayer" -e "mplayer %U"
Icon=gnome-mplayer
StartupNotify=true
Terminal=false
Type=Application
...

```


In ~/.local/share/applications/mimeapps.list


```

[Added Associations]
...
[Default Applications]
...
audio/x-mp3=console-mplayer.desktop                   
...

```

---

