---
title: "how to run starcraft with wine"
date: 2005-05-05
forum: Gaming &amp; Leisure
---

### Post by pdk001 on 2005-05-05
i've successfully done i wanted things in ubuntu, linux now im trying to run starcraft game with wine in linux
im exactly don't know how to do, i need you guys help again
please give me a tip such as need SC cd(?),(i dont need CD when i play this game in windows because of using CDSPACE program), winetools and something else
any tips or ideas would be appreciated

-pdk-

---

### Post by Rodrigo on 2005-05-05
Go to your /media/cdrom and run the setup with wine, install it like you would on Win (C:\ProgramFiles\Starcraft).
Now to play starcraft, goto the terminal, then go to the .wine directory

dude@mypc:/home/dude$: cd .wine
then go to drive_c/ProgramFiles/Starcraft
and wine theprogramtolaunchSCwichIcantrememberthename.exe

---

### Post by pdk001 on 2005-05-05
thanks you for replay
i have a starcraft.LCD(i didnt burn SC as booting CD) and can you teach me how can i move that "program files" dir -  this is have a blank
i would greatly appreciate if you explain this easily

-pdk-

---

### Post by Rodrigo on 2005-05-06
As you know wine emulates windows exe files,
If you install a windows program, where would it be instaled?
Normally in windows like this: Driveletter:\Thefolderordirectorythathasyourprogramfiles\thefolderordirectorywiththenameofthefile
(in my case: C:\Archivos de programa\Starcraft, yes, its spanish)

right?

since the linux directory tree will never be like win dir tree, then wine creates a "hidden folder" (dot file for the techies  :razz:, all files that start with a dot are hidden files ) and creates a similar structurure WITHIN the folder of wine (wich is hidden too)

so where is this hidden wine folder?

in your username folder

in my case: /home/Rodrigo/.wine

ok?

you can go to .wine any time just with cd, "cd .wine"
in there you will find a folder named drive_c/, guess what? thats your c: drive  :grin: 

got it?

---

