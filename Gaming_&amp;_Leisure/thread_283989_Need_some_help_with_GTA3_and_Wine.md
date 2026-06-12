---
title: "Need some help with GTA3 and Wine"
date: 2006-10-24
forum: Gaming &amp; Leisure
---

### Post by Motoxrdude on 2006-10-24
Hey, I installed wine, and GTA3. When I go to execute the gta3.exe files, i get this error message:
```

err:module:import_dll Library  (which is needed by L"C:\\Program_Files\\Rockstar_Games\\GTAIII\\gta3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program_Files\\Rockstar_Games\\GTAIII\\gta3.exe" failed, status c0000135

```
I have no clue what to do. Any help will greatly be aprreciated!
I am using ubuntu dapper btw.

---

### Post by Motoxrdude on 2006-10-25
bump

---

### Post by Motoxrdude on 2006-10-26
bump bump bump

---

### Post by gerowen on 2006-10-27
Make sure you have a copy of [mfc42.dll](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42) in $HOME/.wine/drive_c/windows , and that you have copies of [riched20.dll](http://www.dll-files.com/dllindex/dll-files.shtml?riched20) and [riched32.dll](http://www.dll-files.com/dllindex/dll-files.shtml?riched32) in $HOME/.wine/windows/system32.

You could also try launching the game with the -opengl option, may solve some issues.

---

