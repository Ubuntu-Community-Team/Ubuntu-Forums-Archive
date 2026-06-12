---
title: "Diablo II LOD Execute Problems"
date: 2006-03-21
forum: Gaming &amp; Leisure
---

### Post by mstlyevil on 2006-03-21
I successfully installed D2LOD on Dapper using Wine. I also installed a cd crack and created a bash script to execute it. When I try to execute it I get this error.

```
pantera@Dapper:~/.wine/drive_c/Program Files/Diablo II$ ./D2.sh
mv: `Diablo II.exe' and `Diablo II.exe' are the same file
wine: cannot find 'Diablo\ II.exe'
mv: cannot stat `Diablo II1.exe': No such file or directory
pantera@Dapper:~/.wine/drive_c/Program Files/Diablo II$ wine Diablo\ II.exe
wine: could not load L"c:\\windows\\system32\\Diablo II.exe": Module not found
pantera@Dapper:~/.wine/drive_c/Program Files/Diablo II$ gedit D2.sh
pantera@Dapper:~/.wine/drive_c/Program Files/Diablo II$ ./D2.sh
mv: cannot stat `Diablo II.exe': No such file or directory
wine: cannot find 'Diablo\ II.exe'
mv: cannot stat `Diablo II1.exe': No such file or directory

```

Here is the bash script I created.

```
#!/bin/sh
mv -f Diablo\ II.exe Diablo\ II.exe
mv -f Game_crack.exe Diablo\ II.exe
wine "Diablo\ II.exe" &
sleep 2
mv -f Diablo\ II.exe Game_crack.exe
mv -f Diablo\ II1.exe Diablo\ II.exe
exit

```

What am I doing wrong here? Has some one else got LOD to execute using wine? If so, could you tell me how to do it. Your help would be much appreciated.

---

### Post by colo on 2006-03-21
With wine 0.9.9 and Diablo 2 1.11, you don't need any modified versions of the game's binaries, just a properly set up wine (and a original play-CD to run the game).

[http://appdb.winehq.org/appview.php?versionId=49](http://appdb.winehq.org/appview.php?versionId=49) should help you get started.

---

### Post by mstlyevil on 2006-03-21
[QUOTE=colo]With wine 0.9.9 and Diablo 2 1.11, you don't need any modified versions of the game's binaries, just a properly set up wine (and a original play-CD to run the game).

[http://appdb.winehq.org/appview.php?versionId=49](http://appdb.winehq.org/appview.php?versionId=49) should help you get started.[/QUOTE]

Thank you very much.

---

