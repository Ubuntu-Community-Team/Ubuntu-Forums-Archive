---
title: "a strange error on the 26 percent steam update"
date: 2006-09-25
forum: Gaming &amp; Leisure
---

### Post by JediSpam on 2006-09-25
i have used 

wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14

and im getting

wine: could not load L"c:\\windows\\system32\\SteamTMP.exe": Module not found

any ideas ?

---

### Post by Iarwain ben-adar on 2006-09-25
Try this
```
wine "C:\Program Files\Steam\SteamTmp.exe" SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
;-)


Iarwain

---

### Post by delta99 on 2006-09-25
> **Iarwain ben-adar said:**
> Try this
```
wine "C:\Program Files\Steam\SteamTmp.exe" SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
;-)


Iarwain

Got me too! That's ^ how mine worked :)

---

### Post by bugz0r on 2006-09-25
CS is not working. Whenever I launch CS, I arrive at my login screen.

---

### Post by terryfunk4life on 2006-09-28
Ok since i am getting the same problem and none of the methods above are working i get this error wine: cannot find 'C:\Program Files\Steam\SteamTmp.exe'




i beg of you please help i have not played the specialist in 3 weeks!!!!

---

### Post by Iarwain ben-adar on 2006-09-29
Are you sure you have SteamTmp.exe?

Maybe you installed steam into a different folder?


Iarwain

---

### Post by tiberius147 on 2006-10-03
How in the hell do you set up a c:/ drive for linux inyways i just made it Z:/tmp/steam and ofcourse it didnt work cuz there is no c:windows\System32 directory and nor is there a c:/ iny thing cuz linux doesnt use c:/ so wtf!!!!!!!!](*,)

---

### Post by bugz0r on 2006-10-03
You need [Wine](http://www.winehq.com).

---

### Post by tiberius147 on 2006-10-04
i have it! i just am not sure there is a fake c:\ drive or i dont know how to set one up

---

### Post by maniacmusician on 2006-10-04
its in a hidden folder inside your home folder. ".wine" i think, maybe. just look for something wine related. and inside there is a fake c drive.

---

### Post by haxer on 2006-10-04
Maybe try [www.google.se/no/dk/com?](www.google.se/no/dk/com?)

---

