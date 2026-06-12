---
title: "N2N Karmic 9.10 AMD64 Games InDaComputa"
date: 2010-02-10
forum: Gaming &amp; Leisure
---

### Post by UbuAli on 2010-02-10
[COLOR=DarkRed]**N2N**[/COLOR] = **N**ewbie **2** **N**ewbie so now you know.

This Thread contains information about Games.



Ubuntu Gamers Installation Guides
[http://gwos.org/doku.php/guides:start](http://gwos.org/doku.php/guides:start)

Games self installed:
Neverwinter Nights 1
ManiaDrive 1.2


**so lets start**

------------------------------------------------------------------------------------------------------
**default**
------------------------------------------------------------------------------------------------------
Used Ubuntu : kernel 2.6.31-19 karmic amd64


You need for typing work sometimes the Terminal which could be located here

[COLOR=SeaGreen]Anwendungen -> Zubhör -> Terminal
Application -> Accessories -> Terminal
[/COLOR]
You could make a shortcut to your desktop by right click and select the proper command to make a shortcut to your desktop.


If you are lazy in typing sudo command command command

[COLOR=Purple]type[/COLOR]
[COLOR=DarkRed]sudo -s[/COLOR]
password

therefore you are root user and don't need to sudo every action.

Sometimes the text is using sudo and sometimes not. So it could be required to sudo commands to get them to work properly if you didn't used sudo -s.
Better you do sudo -s
------------------------------------------------------------------------------------------------------
**Neverwinter Nights 1 **
------------------------------------------------------------------------------------------------------
First i downloaded all .tar files from the Linux-Version unpacked everything as descriped and had problems with the CD-Key of my Version.
Also the Monitor fade to black (Out of Range) while a wrong Refresh Rate is set by default.
My todos to get it work for 3 in 1 Box "European"/PC-DVD Version.

Before installation :: 32-bit layer is needed (for AMD64)
or you get errors like ./nvn could not open/find ./nvmain

Open Terminal

[COLOR=Purple]type[/COLOR]

[COLOR=DarkRed]sudo apt-get update && sudo apt-get upgrade
sudo apt-get install ia32-libs[/COLOR]

NOW

1. Install Wine (Software Center -> Games -> Wine)
2. Install Neverwinter Nights (with wine-applicationstarter (<- mount/DVDdrive:: right click autorun.exe file, select first entry))
3. Open Places -> Computer
4. Open Filesystem
5. change to home/useraccount/
6. click View -> show hidden files -> check on
7. change to .wine/drive_c/Progam Files/BioWare Corp/Neverwinter Nights
8. Copied following files and folders to a new Desktop folder nwn
---Files and Folders to copy ---
[COLOR=Sienna]
[/COLOR] [COLOR=Sienna]ambient/*
data/*
dmvault/*
hak/*
localvault/*
modules/*
music/*
nwm/*
override/*
portraits/*
saves/*
servervault/*
texturepacks/*
chitin.key[/COLOR]
[COLOR=Sienna]patch.key[/COLOR]   <--- This one isn't in the folder *read beneath*
[COLOR=Sienna]dialog.tlk[/COLOR]
[COLOR=Sienna]dialogF.tlk[/COLOR] (French, German, Italian, and Spanish)

*but there are*
[COLOR=Sienna]xp1.key
xp1patch.key
xp2.key
xp2patch.key[/COLOR]

---Files and Folders to copy ---
 


9. Download and Unpack to Desktop folder nwn :: User Account Required
Linux Client 1.29 binaries (nwclient129.tar.gz)

Read here
[http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)

10. Download Patch and unpack to Desktop folder nwn
**YOU COULD CHOOSE HERE THE PROPER ONE READ NOTES TOO ([COLOR=DarkRed]IMPORTANT[/COLOR])**
[http://nwn.bioware.com/support/patch.html](http://nwn.bioware.com/support/patch.html)


**MYTODO**
[http://files.bioware.com/neverwinternights/updates/linux/168/German_linuxclient168_xp2.tar.gz](http://files.bioware.com/neverwinternights/updates/linux/168/German_linuxclient168_xp2.tar.gz)

Yes i downloaded the wrong one at first, just for NWN1. 
So i renamed xp2patch.key in folder Desktop nwn -> patch.key and didn't extract the patch.key file from the update. Next time i take the link from
above and i didn't have to rename anything.

11. Open Terminal
12. change to Desktop/nwn

[COLOR=Purple]type[/COLOR]

[COLOR=DarkRed]./fixinstall[/COLOR]

that should print something like
Fixing case
...
Checking for problem files
...
Checking for permissions
...
You are ready to run Neverwinter Nights.

[COLOR=Purple]type[/COLOR]

[COLOR=DarkRed]./nwn[/COLOR]

Enjoy

More/other NWN1 ways + Desktop Icon here
[http://gwos.org/doku.php/guides:64bit:nwn](http://gwos.org/doku.php/guides:64bit:nwn)

NWN1 BioWare Forum here
[http://nwn.bioware.com/forums/viewforum.html?forum=72](http://nwn.bioware.com/forums/viewforum.html?forum=72)

More/other NWN1 ways + Movies enabled (Platinum and Diamond Edition)
[http://ubuntuforums.org/showthread.php?t=113259](http://ubuntuforums.org/showthread.php?t=113259)

------------------------------------------------------------------------------------------------------
**ManiaDrive 1.2**
------------------------------------------------------------------------------------------------------
Trackmania like game.

Maybe you need this one too i dont know
----------------------------------------
32-bit layer

Open Terminal

[COLOR=Purple]type[/COLOR]

[COLOR=DarkRed]sudo apt-get update && sudo apt-get upgrade
sudo apt-get install ia32-libs[/COLOR]
----------------------------------------

Website:
[http://maniadrive.raydium.org](http://maniadrive.raydium.org)

Download Static Version
[http://prdownloads.sourceforge.net/maniadrive/ManiaDrive-1.2-linux-i386.tar.gz?download](http://prdownloads.sourceforge.net/maniadrive/ManiaDrive-1.2-linux-i386.tar.gz?download)

unpack to a folder

open terminal
change to folder 

[COLOR=Purple]type[/COLOR]

[COLOR=DarkRed]./mania_drive.sh[/COLOR]

or

[COLOR=DarkRed]sh mania_drive.sh[/COLOR]

------------------------------------------------------------------------------------------------------
**UbuAli other Beans**
------------------------------------------------------------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1393882](http://ubuntuforums.org/showthread.php?t=1393882) DMX6Fire 24/96
[http://ubuntuforums.org/showthread.php?t=1395997](http://ubuntuforums.org/showthread.php?t=1395997) Nvidia

---

