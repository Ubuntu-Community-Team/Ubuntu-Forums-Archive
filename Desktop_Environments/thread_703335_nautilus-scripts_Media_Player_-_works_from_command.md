---
title: "nautilus-scripts: Media Player - works from commandline, not from nautilus"
date: 2008-02-21
forum: Desktop Environments
---

### Post by Redsandro on 2008-02-21
Hi,

I am trying to play files through a media player on my tv by rightclicking selected files and choose a script from the *scripts* menu option. For that, I need to open a new layout. I figured this script will do the job:

```
#!/bin/bash

if [ -z $1 ]; then # No files selected
    zenity --error --title "No files selected" --text "Select some files to play on TV."; 
    exit;
else
    gksudo xhost +;gksudo xinit vlc -fs \"$1\" -- :1 -layout tv
fi
```

The error msg works, but when I select files, nothing happens. However, from the command line it DOES work:
```
sander@MC-RED:~$ sudo xhost +;sudo xinit vlc -fs \"$1\" -- :1 -layout tv
```

Ofcourse, nothing plays because the commandline does not make sense in this way, but at least it starts vlc on the television.



2 questions:

1: How do I make this script work? (using sudo in stead of gksudo makes no difference)
2: Can I disable *access control* (xhost +) by default? It's kind of lame to type my password everytime anyone wants to watch a video file.

---

