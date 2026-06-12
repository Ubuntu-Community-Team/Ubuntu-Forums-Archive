---
title: "Permissions - wht do I do"
date: 2005-10-18
forum: Desktop Environments
---

### Post by peterthewolf on 2005-10-18
I am logged on as peter a windows program WinWordFind.exe is in /home/peter/winword. If I double click the exe via file browser the program works. When I set up an application menu entry for it with the following command /home/peter/winword WinWordFind.exe in the menu entry it fails with the following
Details: Failed to execute child process "/home/peter/winword" (Permission denied)
How is it that I do not have permission to use files that belong to me in my folders. I have checked the permissions of all files involved and they are all owned by peter.

---

### Post by bluck on 2005-10-18
[QUOTE=peterthewolf]I am logged on as peter a windows program WinWordFind.exe is in /home/peter/winword. If I double click the exe via file browser the program works. When I set up an application menu entry for it with the following command /home/peter/winword WinWordFind.exe in the menu entry it fails with the following
Details: Failed to execute child process "/home/peter/winword" (Permission denied)
How is it that I do not have permission to use files that belong to me in my folders. I have checked the permissions of all files involved and they are all owned by peter.[/QUOTE]

first off, when you typed "/home/peter/winword  WinWordFind.exe" this is specifying the dir /home/peter/winword as the command with WinWordFind.exe as a parameter for that command,  which isnt what you're trying to do.

you're *trying * to do /home/peter/winword/WinWordFind.exe", which will likely not work either, unfortunately :)

when you double click the app in the browser, it works using wine (likely)

so try specifying this for the command:
wine /home/peter/winword/WinWordFind.exe

hope this helps :)

---

### Post by Pablo_Escobar on 2005-10-18
1. Linux executables do not have the "exe" extension :)
2. Try "/home/peter/winword/WinWordFind"

---

### Post by peterthewolf on 2005-10-18
No dice
Bluck. No response from choosing menu option at all. Yes I am using wine.

Pablo. Using the .exe or not makes no difference. If I put / between winword and WinWordFind I get 
Details: Failed to execute child process "/home/peter/winword/WinWordFind" (No such file or directory)

---

### Post by GeneralZod on 2005-10-18
Edit:

Whoops - bluck said everything I was going to :)

Edit2:

As per bluck's suggestion, try just typing

```

wine /home/peter/winword/WinWordFind.exe

```

on the command-line, and see if any errors show up.

---

### Post by peterthewolf on 2005-10-18
I used synaptic to uninstall wine so that I could reinstall just in case a previous bad install was the problem. On trying to reinstall it fails with the following
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.0.20050628-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.0.20050628-1ubuntu1_i386.deb)
  404 Not Found [IP: 130.239.18.142 80]
So until that is back on line I cannot try anything.

---

