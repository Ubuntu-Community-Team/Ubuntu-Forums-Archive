---
title: "haveing trouble installing steam"
date: 2005-11-14
forum: Gaming &amp; Leisure
---

### Post by Nicktu on 2005-11-14
im haveing some trouble installing steam, i looked at the installation manual for it and its seems to complicated. i cant seem to figure it out 

link to manual:
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17)

can someone please help me, or simplify it for me, ive only gotten to the point of installing wine, i cant install the mozilla plugin :(

---

### Post by unkemptwolf on 2005-11-15
Ive been having the same problem. I can download steam and install it fine (I'm using wine .91), but when I try to start it, it begins downloading the mozilla plugin. Which is fine, it downloads it and launches the installer automatically. But once i get into the install, I run into a problem. It asks me for the location of my mozilla folder, and when I tell it what the location is, it promptly informs me that I am wrong and the install did not complete correctly. When I try to start Steam again, the whole process starts over.

This is true both of the Ubuntu mozilla package, and the windows. I thought perhaps that, being a windows program, it might need the windows version of mozilla, but the same thing happened. Its quite frustrating. Anyone have any suggestions? Anyone gotten it working and could share EXACTALLY how they did it? Thanks.

---

### Post by markmark on 2005-11-16
Did you try installing the mozilla plugin thing yourself manually as described in the guide linked above?

download this file: [http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz](http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz)

extract it to some place within your wine install such as: ~/.wine/drive_c/Program\ Files/mozcontrol

then cd into that directory and run: ```
wine regsvr32 mozctlx.dll
```

Just watch out that I think that *.tgz file has the mozcontrol directory in it, so if you can't find all the files check that you don't have "Program\ Files/mozcontrol/mozcontrol"

---

### Post by unkemptwolf on 2005-11-16
It worked! Now.. to get DoD running:D

---

### Post by Falklian on 2005-11-22
I just installed Steam today and decided to search on how to get the Mozilla plugin installed and found this thread.  Works well enough to get it running, but the problem I'm experiencing now is that although it now loads up, I get no text whatsoever, so I have no idea what to click on etc.  Is this a problem with fonts?  (i.e. don't have the associated fonts the program needs installed on my machine?)

---

### Post by stoffe on 2005-11-22
[QUOTE=Falklian]I just installed Steam today and decided to search on how to get the Mozilla plugin installed and found this thread.  Works well enough to get it running, but the problem I'm experiencing now is that although it now loads up, I get no text whatsoever, so I have no idea what to click on etc.  Is this a problem with fonts?  (i.e. don't have the associated fonts the program needs installed on my machine?)[/QUOTE]
Yes, you need the Tahoma font: [http://www.ubuntuforums.org/showthread.php?t=82318](http://www.ubuntuforums.org/showthread.php?t=82318) 

Alternatively, you can tell Wine to use some other font that you do have, but I don't remember how. Try google. :)

---

### Post by Xyxex on 2005-11-23
well i did just that what we said in this thread, but then when i go in to the "Steam folder" and type: wine Steam.exe  the program doesnt appear.... it happens nothing... what is the wrong?

---

### Post by Xyxex on 2005-11-23
ok now i can start Steam.exe,,, but lol, when i need to put in my account name and password i cant use my keyboard!!! I cant type in anything....

---

### Post by PrincessPeach on 2005-11-24
[QUOTE=Xyxex]ok now i can start Steam.exe,,, but lol, when i need to put in my account name and password i cant use my keyboard!!! I cant type in anything....[/QUOTE]

I had that same problem.  I did some right-clicking in the text fields and restarted it a couple of times and then it worked.

---

### Post by Akya on 2005-12-10
r some reason its giving me an error saying i dont have the authority

---

### Post by Gray. on 2005-12-10
What do you mean? At what part of installing/running Steam do you get this error?

---

### Post by Akya on 2005-12-10
when i try to start it actualy its saying it, it says "Steam.exe (main exception): Win32 StructuredException at 7D49FB71 : Attempt to read from virtual address 88 without appropriate access rights."

---

### Post by Gray. on 2005-12-10
Are you following [this]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17") guide? Make sure that you download the latest Wine (0.9.3). If you edit your sources list (using Terminal):
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_original
sudo gedit /etc/apt/sources.list
```
add the following lines to the end of the file:
```
deb http://wine.sourceforge.net/apt/ binary/
```
then save it and exit.
Now:
```
sudo apt-get update
```
Then open Synaptic (System > Administration > Synaptic Package Manager) and search for wine then select the latest entry and click Apply.
That way Wine should be installed.

---

### Post by Akya on 2005-12-10
dangit! now im having another problem "fatal error: could not load module 'bin/vgui2.dll' "

---

### Post by Akya on 2005-12-10
grey you are very helpfull would you happen to have a screen name or something?

---

### Post by linkunderscore on 2005-12-10
[QUOTE=Akya]dangit! now im having another problem "fatal error: could not load module 'bin/vgui2.dll' "[/QUOTE]


you have to run steam from inside that directory. 

aka

cd ~drive_c/Program Files/SteamApps/Steam/

once you are in that dir do "wine Steam.exe"

---

