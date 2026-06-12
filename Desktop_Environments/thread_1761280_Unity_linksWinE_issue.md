---
title: "Unity links/WinE issue"
date: 2011-05-17
forum: Desktop Environments
---

### Post by askedmarlin on 2011-05-17
I un-installed WinE earlier today, however Unity still holds dead links which I have not been able to remove.

I have no clue how to remove the links. I have tried reinstalling & removing WinE both with & without the added programs, but no luck.

I am using Wubi + Ubuntu 11.04

[IMG]http://askedmarlin.webs.com/shorts.jpg[/IMG]

---

### Post by mc4man on 2011-05-17
There is a couple of places to look in - 
Open your home folder (view > show hidden files), > .local/share/applications
Look for files directly in there - <whatever>.desktop's and or icons with relevant names.
Also there may be a wine folder, look inside.
Delete anything related to what you don't want in the dash

---

### Post by askedmarlin on 2011-05-18
> **mc4man said:**
> There is a couple of places to look in - 
Open your home folder (view > show hidden files), > .local/share/applications
Look for files directly in there - <whatever>.desktop's and or icons with relevant names.
Also there may be a wine folder, look inside.
Delete anything related to what you don't want in the dash

Unfortunately I've already tried that, but the links aren't there. :/
I checked the path(s) that the links within Unity point to, but I don't know what to do from there

```

application://wine-Programs-[program-name-here.desktop]
 
```

---

### Post by practic on 2011-05-18
Did you also look in /usr/share/applications? 

Remember that the files you see in that directory may look a bit different than what they are actually named...the ".desktop" extension will be hidden, and the name will be shown from value of "Name=" within the .desktop file. 

So, for example, the shortcut for  "acroread.desktop" in usr/share/applications shows up in Nautilus as "Acrobat Reader 9".

I found it handy to use the "open with GEdit as Root" Nautilus script, so I could just right-click on these .desktop files, choose "Scripts" from the menu, the "Open with Gedit as root".

---

### Post by askedmarlin on 2011-05-18
> **practic said:**
> Did you also look in /usr/share/applications? 

Remember that the files you see in that directory may look a bit different than what they are actually named...the ".desktop" extension will be hidden, and the name will be shown from value of "Name=" within the .desktop file. 

So, for example, the shortcut for  "acroread.desktop" in usr/share/applications shows up in Nautilus as "Acrobat Reader 9".

I found it handy to use the "open with GEdit as Root" Nautilus script, so I could just right-click on these .desktop files, choose "Scripts" from the menu, the "Open with Gedit as root".

No luck. :/

Defaults.list does not contain them either.

---

### Post by mc4man on 2011-05-18
Well if they're showing up in the applications dash the files are somewhere.

You could try opening  the old gnome search
gnome-search-tool
and searching for .desktop
system wise that may produce a couple of thousand results, scroll thru and see.

If you wanted to narrow this down a bit first you could temp create a new user w/ users and groups, log in to that user and ck. there.
If they don't show up then the files are  in your home dir., if they do then the files are in the system files somewhere - /usr/, /usr/local/ or /opt/
(then delete that temp user in users and groups


Edit: I've never used wubi so - how where you using itunes previously (was it installed or did you use one on the windows system?

---

### Post by Krytarik on 2011-05-18
I'm quite sure that all related files are solely in your home directory.

Wine menus/launchers are stored in these directories, maybe even more ;-), listed in the order of the directory tree:

~/.config/menus/applications-merged
~/.local/share/applications
~/.local/share/applications/wine
~/.local/share/desktop-directories
~/.local/share/icons
~/.wine/drive_c/users/Public/Desktop
~/.wine/drive_c/users/Public/Start Menu/Programs
~/.wine/drive_c/users/<USER>/Desktop
~/.wine/drive_c/users/<USER>/Start Menu/Programs

Good luck!

---

### Post by askedmarlin on 2011-05-18
> **Krytarik said:**
> I'm quite sure that all related files are solely in your home directory.

Wine menus/launchers are stored in these directories, maybe even more ;-), listed in the order of the directory tree:

~/.config/menus/applications-merged
~/.local/share/applications
~/.local/share/applications/wine
~/.local/share/desktop-directories
~/.local/share/icons
~/.wine/drive_c/users/Public/Desktop
~/.wine/drive_c/users/Public/Start Menu/Programs
~/.wine/drive_c/users/<USER>/Desktop
~/.wine/drive_c/users/<USER>/Start Menu/Programs

Good luck!
Thanks for the help!

The dirs. were helpful and I found more references to WinE within a few, but I couldn't fix the problem. Fortunately I found a .disk backup without this bug that I can run my system from, so I just transfered my files to it.

-Marlin

---

