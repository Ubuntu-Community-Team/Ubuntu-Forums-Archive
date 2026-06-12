---
title: "Doom 3 res and shortcut"
date: 2013-04-05
forum: Gaming &amp; Leisure
---

### Post by Dallas2coolio on 2013-04-05
I tried installing Doom 3 using my CD but for some reason the CD won't install when it tried to install the game files so I tried to do was copy the game files on my Sony notebook and put it on my Ubuntu on my netbook but just didn't know exactly where to put the folder. I just for now put it in the doc folder and I tried to make a shortcut to the desktop but it won't work since it won't link to the Doom 3 folder.   Also another problem is that once I open the game and exit it the res stays at 640x480 and doesn't go back to the normal desktop res which is 1024x600 for my netbook.    EDIT:  I fixed the res problem I just had to set the display to laptop and make it sticky.   But still I need to find a place to put the folder and to make a shortcut to the desktop.

---

### Post by Dallas2coolio on 2013-04-05
Does anyone know where I should put the game folder and how to create a shortcut to desktop so I can open the game on the desktop. All I can say that I can't put it on the file system I thought that's where it would go but maybe there is a spot for programs to go in. Also when I tried to copy the game icon from the Doom 3 folder it doesn't work. I have to somehow link that shortcut to the game icon on the folder.

---

### Post by Dallas2coolio on 2013-04-05
If no one knows where does all program files go normaly like where would the WoW game I installed goto? I assume it's in the file system folder but I don't know where. I thought maybe I should put it there where the WoW game is at. I' am surprised that 70 views and no one knows.

---

### Post by oldos2er on 2013-04-06
Have you seen [https://help.ubuntu.com/community/Doom3](https://help.ubuntu.com/community/Doom3) ?

---

### Post by Dallas2coolio on 2013-04-06
I' am trying to figure out what that site meant about installing Doom 3 but I' am actualy confused. What is the easiest way to install Doom 3 on the Ubuntu? I have only done so far is transfer the Doom 3 folder from my other computer to this netbook and it works fine but just need to be able to able to make a shortcut file so I can just double click on it and open the game rather than going to the game folder and running it from there.

---

### Post by oldos2er on 2013-04-07
If you're using Unity, see [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

---

### Post by SingingBush on 2013-04-08
You'll need something like this:

```
#!/usr/bin/env xdg-open


[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=/usr/local/bin/doom3 +set s_alsa_pcm plughw:0 +set NumberOfSpeakers 6 "$@"
Name=Doom 3
Name[en_GB]=Doom 3
Icon=/usr/share/icons/hicolor/256x256/apps/doom3.png

```

---

