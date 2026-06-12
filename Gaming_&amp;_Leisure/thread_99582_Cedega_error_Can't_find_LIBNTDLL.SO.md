---
title: "Cedega error: Can't find LIBNTDLL.SO"
date: 2005-12-05
forum: Gaming &amp; Leisure
---

### Post by anil_robo on 2005-12-05
I installed Cedega somehow, and after a long search, found it lying in my home/bin directory. I was trying to run DiabloII: LOD by the following steps:
1. Inserted original game CD in drive --> mounted automatically
2. Game already installed in windows NTFS partition--> mounted that too (read only)
3. Opened terminal and typed command to run game with the following result:
```

akumar@akumar:~/bin$ /home/akumar/.WineCVS/installs/cvscedega/bin/wine
/home/akumar/.WineCVS/installs/cvscedega/bin/wine: error while
 loading shared libraries: libntdll.so: cannot open shared object file:
 No such file or directory

``` 
Why this problem? Is it because:
- I installed the game in windows, not cedega?
- I installed cedega the incorrect way (installed in my bin directory)?
- The windows partition where game is installed is mounted read-only?

By the way, when I type cedega and press enter in the terminal, nothing happens. To run cedega, I have to go to my bin directory and type ./cvscedega and then it runs, asking for file.

Someone please help, and I'll get rid of windows for ever!

---

### Post by claydoh on 2005-12-05
definitely it is because it is not installed under cedega, and I am sure the read-only part is not helping any, either unfortunatley.

If you have cvscedega in ~/bin, you *should* just have to type "cvscedega" from a terminal

---

### Post by anil_robo on 2005-12-06
I realized that, CLaydoh, and copied cvscedega.sh from user's bin directory to root's bin directory. Typing cvscedega from terminal now "does something". I gave the command to cedega to run DiabloII:LOD, and here's the output:
```

akumar@akumar:/media/WinPrograms/Program Files/Diablo II$ cvscedega Diablo\ II.exe
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
/home/akumar/.WineCVS/installs/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804c95c)
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
wine: Unhandled exception, starting debugger...
err:ntdll:MODULE_THREAD_WaitThreadModuleSafe this should never happen. (unless wine crashed)
err:ntdll:MODULE_THREAD_WaitThreadModuleSafe this should never happen. (unless wine crashed)
err:ntdll:MODULE_THREAD_WaitThreadModuleSafe this should never happen. (unless wine crashed)
tid 10502 received signal 2. Raising signal 3
tid 10508 received signal 2. Raising signal 3
/bin/cvscedega: line 108: 10502 Quit                    "$ConfigurePrefix/bin/$WineExecName" "$@"

``` 
I could see that cedega was trying to read/write (?) from the root owned folders. So I became root (sudo su) and then ran cvscedega command. This is the output:

```

root@akumar:/media/WinPrograms/Program files/diablo II# cvscedega game.exe

Enter Path for first Drive (C:) (Default: /root/.cvscedega/drive_c)
Newbies, press enter

Making fake C drive...


Edit the /root/.cvscedega/config file to fit your system

Installing registry...
Done
/home/akumar/.WineCVS/installs/cvscedega/bin/wine: cannot find 'game.exe'

``` 

apparently, cedega has been set up correctly. I noticed that there were two files in diabloII:LOD directory: game.exe and diablo II.exe
I ran diabloII.exe and there was a dialog box saying "please make sure the game CDROM is in the drive"

Why doesn't wine/cedega recognize diablo CD? i have bought the original CD, and it doesnt' work in Linux, but works perfectly in windows.
Is there a way I can run DiabloII:LOD under Linux and get rid of windows permanently?

---

### Post by claydoh on 2005-12-06
I am not sure how to set up cvscedega (I have a subscription to Cedega) but I think you may need to edit a configuration file setting up the location of your cdrom. I am not sure how this is done as now cedega uses a gui and seems to get that all sorted out automatically.

look [here]("http://cedegawiki.sweetleafstudios.com/wiki/Diablo2") and [here]("http://transgaming.org/forum/viewforum.php?f=32&sid=b7c471018025af2950b62907d1242489") for more info/help

---

