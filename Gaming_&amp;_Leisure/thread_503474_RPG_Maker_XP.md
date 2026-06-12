---
title: "RPG Maker XP"
date: 2007-07-17
forum: Gaming &amp; Leisure
---

### Post by treeko11 on 2007-07-17
Hi everyone,

I just installed rpg maker XP using wine, and it installed perfectly except that when i try to start it up nothing happens... Any help?

Also is the any way to check what processes are running, like task manager in windows?:popcorn:

---

### Post by kknd on 2007-07-17
There is the System monitor, in Sistem -> Admin

---

### Post by KhaaL on 2007-07-18
Could you post the terminal output when you try to run it?

---

### Post by treeko11 on 2007-07-18
ok, here it is

> wine /home/computer/.wine/drive_c/Programfiles/Enterbrain/RPGXP/RPGXP.exe
err:module:import_dll Library rgss102e.dll (which is needed by L"C:\\Programfiles\\Enterbrain\\RPGXP\\RPGXP.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Programfiles\\Enterbrain\\RPGXP\\RPGXP.exe" failed, status c0000135


EDIT: I just looked at it and im trying to download the dll it requests.

EDIT2: Ok i downloaded and put the stuff in the folder but now it wants me to install RGSS-RTP Standard, which i have.

---

### Post by cogadh on 2007-07-18
When you launch RPG Maker, change to the application's install directory first. Most Windows application need to be launched from within their install directory to work correctly, otherwise they often can't find needed files. For example, don't do this:
```
wine $HOME/.wine/drive_c/Program\ Files/Enterbrain/RPGXP/RPGXP.exe
```
Instead do this:
```
cd $HOME/.wine/drive_c/Program\ Files/Enterbrain/RPGXP/
wine RPGXP.exe
```

EDIT - Almost forgot, the application produces the same missing DLL error on Windows if you try to run it before you install RGSS-RTP Standard, which has to be installed separately from the main application.

---

### Post by treeko11 on 2007-07-18
ok, thanks, but i already have installed rgss-rtp

---

### Post by cogadh on 2007-07-18
Then try the suggestion I made about changing directories. Like I said, the application may not be able to find RGSS-RTP Standard since it is not running from within its install directory.

---

### Post by treeko11 on 2007-07-18
so what exactly do i do? im sort of confused... :confused:

---

### Post by cogadh on 2007-07-19
Copy this into the terminal and hit enter:
```
cd $HOME/.wine/drive_c/Program\ Files/Enterbrain/RPGXP/
```
Then run this:
```
wine RPGXP.exe
```

---

### Post by treeko11 on 2007-07-19
wats with the the '\' in program files?

---

### Post by cogadh on 2007-07-19
Its an escape charater that allows the space between "Program" and "Files" to be seen. If you don't use it, you'll get a "can't find directory 'Program'" error.

---

### Post by jerbucket on 2007-07-29
treeko11,

Did you get it to work?

---

### Post by treeko11 on 2007-09-22
no, i didn't...

---

### Post by Mrmental on 2008-01-29
I've managed to get RPG Maker XP to work perfectly. Here's how I did it, on Ubuntu Gutsy:

1: Install the latest Wine .DEB from [budgetdedicated.]("http://wine.budgetdedicated.com/archive/index.html")

2: In a terminal, mount your RPG Maker Disc if it isn't already mounted. Then navigate to it.

3: Within the disc, Navigate to the Setup1 Directory

4: The setup programs are more or less useless on Linux, and you don't need them anyway. Instead, install the .msi file directly by entering
msiexec /i <name of MSI file.>
5: Navigate to the setup2 directory and do the same for the .msi file there.
6: Enjoy!
Note: It is imperative that you install the files in the correct order, first the .msi from the setup1 directory and then the .msi file from the setup2 directory.

This worked wonderfully for me after many minuted of faffing about trying to the install programs to behave.
Once you've done this, the RPG maker program should appear in the wine section of your applications menu.
Hope this helps
SB

---

