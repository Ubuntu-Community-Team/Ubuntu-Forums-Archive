---
title: "How to add custom applications in open with??"
date: 2005-07-10
forum: Desktop Environments
---

### Post by Petrush on 2005-07-10
I have managed to get wine to run a windows player called amazing slow downer. Which I am very happy about.

I have managed to get it to the GNOME applications menu by doing a .desktop file for it.
```

[Desktop Entry]
Name=Amazing Slow Downer
Comment=Play soundfiles at lower speed

Exec=wine /media/Windows/Program\ Files/Roni\ Music/Amazing\ Slow\ Downer/amazing.exe
Type=Application
Categories=Application;AudioVideo
MimeType=audio/basic;audio/mpeg;audio/x-aiff;audio/x-mp3;audio/x-wav;
Terminal=false

``` 

now I want to be able to right click and do "open with". But no success, i get an error saying "Could not add application" - Could not add application to the application database.

What's wrong, its the same MimeType in my .desktop as the file i try to open??

help apriciated.

---

### Post by reuben on 2005-07-10
I don't use gnome. But you could try writing a shell script to launch the program:

#!/bin/bash
wine /media/Windows/Program\ Files/Roni\ Music/Amazing\ Slow\ Downer/amazing.exe

You'll need to deal with the command line argument; i.e. append it to the exec line. My guess is that gnome is balking at the .desktop file being used to call something with command line attributes already. By wrapping it in the script you should be fine.

---

### Post by lorenzo on 2005-07-10
Try to install **smeg** menu editor. You can add your programs and folders to the ubuntu menu. 
After that, the programs you have added to the menu ara availables to "open with".

Ciao,
Lorenzo

---

### Post by Petrush on 2005-07-10
[QUOTE=lorenzo]Try to install **smeg** menu editor. You can add your programs and folders to the ubuntu menu. 
After that, the programs you have added to the menu ara availables to "open with".
[/QUOTE]

Doesn't make any change, I see the application in the list, as before, but when it's selected i get the same error. Strange.

---

### Post by yangeryanger on 2006-12-04
I think it's not that the fact that it's not being listed, but when u attempt to add a command to the "open with" of that type of filetype, it gives you that error.

I'm having that issue as well, with matroska format video.. when i try to associate mkv files with mplayer, it gives me "Could not add application to the application database" as mplayer wasn't on the list...

maybe it's a bug?

---

### Post by owennewo on 2007-01-09
I had the same problem, and found the fix here:
[http://ubuntuforums.org/showthread.php?t=23913](http://ubuntuforums.org/showthread.php?t=23913)

basically a hidden folder (.local) off your home directory is probably owned by root, or has the wrong permissions in my case the following fixed the problem:

sudo i 
[then answer password]
chown -R owen:owen /home/owen/.local

change the user 'owen' to whatever your username is.

---

