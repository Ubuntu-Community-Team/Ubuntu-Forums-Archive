---
title: "Run game without terminal"
date: 2011-07-16
forum: Gaming &amp; Leisure
---

### Post by jadonchristensen on 2011-07-16
Hello, I am trying to start a game without having the terminal popup. I've tried putting & on the end, but then it wont run.

How can I execute/run my game without the terminal?

example launcher:
/home/user/firestorm --login Bob Hope password --port 13002

I am using Xubuntu 11.04.
This is the game (Firestorm) that I am trying to run without the terminal [http://www.phoenixviewer.com/](http://www.phoenixviewer.com/)

Thank you

---

### Post by Toz on 2011-07-16
Create the file **~/.local/share/applications/firestorm.desktop** with the following contents:
```

[Desktop Entry]
Encoding=UTF-8
Exec=/home/user/firestorm --login Bob Hope password --port 13002
Icon=/home/user/secondlife_icon.png
Name=Firestorm                      
NoDisplay=false
Type=Game              
Categories=Game
StartupNotify=true

```

It should show up in your Game submenu.

---

### Post by jadonchristensen on 2011-07-17
I got it working. I just had to right click the Launcher, do Edit Launcher and uncheck "Run in Terminal".

---

