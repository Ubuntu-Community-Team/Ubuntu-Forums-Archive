---
title: "ut2003 install guide. for dummies"
date: 2009-04-18
forum: Gaming &amp; Leisure
---

### Post by PaulReaver on 2009-04-18
This worked for me on intrepid.  


Installing UT2003 in Ubuntu for dummies.

Step 1
Insert Disc 3
Copy linux_installer.sh from Disc 3 to home directory to eg. "/home/<UserName>/linux_installer.sh"
for reference mine was /home/paul/linux_installer.sh

Step 2
Unmount and Eject Disc 3

Step 3
Insert Disc 1 but DO NOT MOUNT

Step 4
in terminal cd to home directory
eg.  "cd /home/<UserName>/"

Step 5
in the same terminal run linux_installer
"sudo _POSIX2_VERSION=199209 linux32 sh ./linux_installer.sh"

You will need to agree to the licence agreement and then you can choose install directories.  Just leave these at the defaults to make things easy. It will also ask if you want to see the README.

Unreal Tournament 2003 will then start installing.  Swap to disc 2 when it asks.  You should be able to open the cd/dvd drive with the button on the actual drive because hopefully you DID NOT MOUNT disc 1.

Step 6
When disk 2 has finished you will be asked in a terminal to insert your cd key.  You will not be able to Input your cdkey. Something to do with bad mojo. Even though it says you will not be able to play the game close the terminal anyway. 

Step 7
You will need to create a text document called /usr/local/games/ut2003/system/CDkey.  In this document insert your CDkey on the first line in this format
"XXXXX-XXXXX-XXXXX-XXXXX"
All uppercase with dashes.
If you are copying using nautilus' GUI you will need to start as sudo
eg.  "sudo nautilus" in a terminal. Remember to grant permissions using right click then scroll down to properties and then click permissions tab.


Step 8 Last step
The libSDL-1.2.so included in the retail package will crash newer ubuntu installs. So we need to delete it from "/usr/local/games/ut2003/system/".  
Copy your libSDL from "/usr/lib/"
for reference mine "was libSDL-1.2.so.0.11.1"
yours may be a different version but
copy it anyway to "/usr/local/games/ut2003/system/"

To Play
Type ut2003 in a terminal

Alternatively create a desktop shortcut by copying and pasting this into an empty file

[Desktop Entry]
Exec=ut2003
Terminal=false
Type=Application
Icon=/usr/local/games/ut2003/Unreal.xpm
Name=ut2003

and saving this as "ut2003.desktop".



bump didley ump.  :)

---

### Post by Vadi on 2009-04-18
Thanks for sharing :)

---

### Post by Shazaam on 2009-04-19
Yes, thank you. Installed and runs fine.

---

