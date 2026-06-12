---
title: "Conquer problem i cant run"
date: 2006-07-19
forum: Gaming &amp; Leisure
---

### Post by CameronCalver on 2006-07-19
hello i downloaded conquer a online game from
[www.conqueronline.com](www.conqueronline.com) and i try to run it will cxoffice and wine and none of them work can someone plz help me

(the file is ruffly 350mb)

---

### Post by x64Jimbo on 2006-07-19
You'll probably want to look for help from the experts at CrossoverOffice and Wine, since most of the people here specialize in Ubuntu-specific solutions. I can tell you that Wine is still very experimental, and should not be considered a complete windows replacement. 
You may want to look into Cedega - It's a Transgaming project that is working on porting pretty much all Windows games to Linux through Wine libraries - but preconfigured.

---

### Post by CameronCalver on 2006-07-19
yes but maybe someone using ubuntu has had the same problem and has found a solution

---

### Post by khado on 2006-07-19
i had a similar,problem
now when i used to play this game in windows,
the download was 600mb,
now the error is actually todo with some missing files,
the missing 200-300mb could be the answer
but i havent find that file yet
sorry

---

### Post by CameronCalver on 2006-07-19
ok well if someone knows the answer to this problem already two people will be happy and khado which exe do u run the conquer.exe or play.exe

---

### Post by CameronCalver on 2006-07-20
ok i have got some good news you now all those errors i have got myn down to one using wine myn is now this
```
cameron@ubuntu:~$ wine /home/cameron/games/conquer/Conquer.exe
err:ole:CoUninitialize Mismatched CoUninitialize
cameron@ubuntu:~$

```


khado paste your eror and ill try to get your errors fixed up

edit: ok now instead of running  conquer.exe run play.exe and it gets up to the bit where you click enter exit or help which is goot then crashes when you click enter it crashes
```
err:ole:CoUninitialize Mismatched CoUninitialize
```

---

### Post by x64Jimbo on 2006-07-20
Most people are reporting this game as "Garbage" at WineHQ. Not saying you won't be able to get it working, but it might be smart to wait a while until the gurus at Wine have done some more tweaking.
[http://appdb.winehq.org/appview.php?iVersionId=4055](http://appdb.winehq.org/appview.php?iVersionId=4055)

---

### Post by CameronCalver on 2006-07-23
and another thing i installed in on crossover and it looked like it was going good but crossover  did not create a windows application in the applications menu so how will i get it to make one or where are the files saved

---

### Post by XVampireX on 2006-07-23
Uhm, more research would have given you the answer: No, it won't work as GameGuard is not supported in WINE/CrossOver/Cedega

---

### Post by CameronCalver on 2006-07-24
ok thanks for that but will it ever be supported?

---

### Post by x64Jimbo on 2006-07-24
Tough to say for sure. You're best off asking the Cedega developers if they will support it in the future. Seeing as their goal is to get all Windows games running in Linux, I would imagine they have at least some sort of plan to support it, but like I said, you'd have to ask them.

---

