---
title: "Minor Wine + Steam Problem"
date: 2005-12-10
forum: Gaming &amp; Leisure
---

### Post by tpnerdcore on 2005-12-10
ok, i want to install steam on wine. I found a guide that's fairly simple on winhq.com. But the thing is i need to install the mozilla active X control thing. And it tells me to unzip to a folder that wine can read. I cant find anywhere physically on my filesystem that says wine. Can anybody help me where this is or how to get to this folder so i can install steam correctly. Thanks 


~/.wine/drive_c/Program\ Files/mozcontrol.

anthony(tpnerdcore)

---

### Post by Gray. on 2005-12-10
Open nautilus (the file browser) and go to your Home Folder.
Press Ctrl+H to show hidden files and folders.
Open the .wine folder.
Open drive_c > Program Files
Make a new directory called mozcontrol.
Thats where you put the files that you unzipped into.
Ask if you have anymore questions.

---

### Post by Akya on 2005-12-10
thanks, but now my steam is installed but it wont start

---

### Post by Gray. on 2005-12-10
What errors does it give when you type
```
cd ~/.wine/drive_c/Program\ Files/Steam && wine Steam.exe
```
*EDITED* correct way to run Steam. Thanks to linkunderscore.

---

### Post by Gray. on 2005-12-10
When I tried to run the above command I got an error about a missing VGUI2.dll or somthing, but when I ran the script I made, it let me boot into CS. If you want that script I can post it here.

---

### Post by linkunderscore on 2005-12-10
[QUOTE=Gray.]When I tried to run the above command I got an error about a missing VGUI2.dll or somthing, but when I ran the script I made, it let me boot into CS. If you want that script I can post it here.[/QUOTE]

you have to run Steam.exe FROM INSIDE THAT DIRECTORY

cd ~/.wine/drive_c/Program\ Files/SteamApps/Steam/

then do "wine Steam.exe"

---

### Post by Gray. on 2005-12-10
its ~/.wine/drive_c/Program\ Files/Steam

and i edited the command to the proper one now thanks.

[Here's]("http://www.ubuntuforums.org/showthread.php?t=94644&page=2&highlight=CS.bash") the link to make a shortcut to start CS.

---

### Post by Akya on 2005-12-10
i did that then it did this 
~/.wine/drive_c/Program Files/Steam$  wine steam
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\PROG~FBU\\MOZI~2E2.12\\mozctl.dll") not found
err:module:import_dll Library MSVCR70.dll (which is needed by L"C:\\Program Files\\Steam\\CSERHelper.dll") not found
err:module:import_dll Library MSVCR70.dll (which is needed by L"C:\\Program Files\\Steam\\CSERHelper.dll") not found
fixme:dbghelp:EnumerateLoadedModules If this happens, bump the number in mod
Shutting down. . .
30client callback thread error
then it gave me an error pop up saying Steam.exe (main exception): Win32 StructureException at 7D7FFb71: Attempt to read from virtual address 88 without appropriate access rights

---

### Post by tpnerdcore on 2005-12-10
well when i want to install steam it asks for layout librarys or something like that:(  does anybody know what to do. I did find how to put a mozcontrol directory in program files thanks for that. Does anybody know about the layout library?

anthony(tpnerdcore)

---

### Post by Gray. on 2005-12-10
Did you run ```
wine regsvr32 mozctlx.dll
``` from the mozcontrol directory? I remember that when I first tried to do it, it said completed but I still got that error. I just retried it again (twice) and then it worked. Maybe it could help you too?

---

### Post by tpnerdcore on 2005-12-11
Well thanks man, but it saiys it failed to find the DLL. Shouldi enter the code abouve after i try to install it again?? Or what. Because i triedto do it and it said the DLL was missing so any sugestions?

thanks
anthony(tpnerdcore)

---

### Post by tpnerdcore on 2005-12-11
Well thanks man, but it saiys it failed to find the DLL. Shouldi enter the code abouve after i try to install it again?? Or what. Because i triedto do it and it said the DLL was missing so any sugestions? :)

thanks
anthony(tpnerdcore)

---

### Post by tpnerdcore on 2005-12-11
sorry for the double post

---

### Post by YokoZar on 2005-12-11
[QUOTE=Akya]i did that then it did this 
~/.wine/drive_c/Program Files/Steam$  wine steam
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\PROG~FBU\\MOZI~2E2.12\\mozctl.dll") not found
err:module:import_dll Library MSVCR70.dll (which is needed by L"C:\\Program Files\\Steam\\CSERHelper.dll") not found
err:module:import_dll Library MSVCR70.dll (which is needed by L"C:\\Program Files\\Steam\\CSERHelper.dll") not found
fixme:dbghelp:EnumerateLoadedModules If this happens, bump the number in mod
Shutting down. . .
30client callback thread error
then it gave me an error pop up saying Steam.exe (main exception): Win32 StructureException at 7D7FFb71: Attempt to read from virtual address 88 without appropriate access rights[/QUOTE]
Did you accidentally do any of this using the sudo command?  Running things as root (do not run Wine as root) will cause files to be owned by root, and make them unreadable by Wine.

Try setting everything in Wine's folder to be owned by your user: sudo chown -r user:user /home/user/.wine

replace user with your username, of course.

---

### Post by tpnerdcore on 2005-12-11
its saying :

anthony@ubuntu:~$ sudo chown -r anthony:anthony /home/anthony/.wine
chown: invalid option -- r
Try `chown --help' for more information.


did i do it right???

anthony(tpnerdcore)

---

### Post by kerm on 2005-12-14
He meant:

```
anthony@ubuntu:~$ sudo chown **-R** anthony:anthony /home/anthony/.wine
```

That way, you will change owner "R"ecursively through the folder.

---

