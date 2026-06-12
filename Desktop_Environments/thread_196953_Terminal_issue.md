---
title: "Terminal issue"
date: 2006-06-15
forum: Desktop Environments
---

### Post by AlmightyMalachi on 2006-06-15
I'm a newbie To Linux. I want to Wine open a program, but i can't get to the directory because theres spaces in the Characters like so

root@Veronica:/home/matt# wine /root/.wine/drive_c/Program Files/iMesh Applications/iMesh6/iMesh6.exe
wine: cannot find '/root/.wine/drive_c/Program'

Help?

---

### Post by 23meg on 2006-06-15
Use quotes```
"/home/matt# wine /root/.wine/drive_c/Program Files/iMesh Applications/iMesh6/iMesh6.exe"
```or a backslash```
/home/matt# wine /root/.wine/drive_c/Program\Files/iMesh Applications/iMesh6/iMesh6.exe
```

---

### Post by frying_fish on 2006-06-15
Also, may I ask why you are trying to run these wine programs as root?

Generally, it is a good idea to run wine things (and in general most programs) as a regular user, letting a program have root access can be bad.  

Once you have installed wine, then as a regular user you can just run "wine /path/to/exe" to install the program to that users home dir under ~/.wine/drive_c/foo  and they can then run it, its a lot better than doing it as root.

Also as 23meg says, you can just put "" around the name for it to deal with spaces, or when you are typing the location type the first bit of each folder, then hit tab as it should auto-complete.

---

