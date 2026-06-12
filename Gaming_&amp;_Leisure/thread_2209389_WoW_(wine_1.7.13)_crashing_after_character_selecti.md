---
title: "WoW (wine 1.7.13) crashing after character selection during load"
date: 2014-03-05
forum: Gaming &amp; Leisure
---

### Post by AlwaysRemind on 2014-03-05
Hey guys! Right before I got rid of Windows 8 I copied my WoW folder and placed it under /home/brandon/. With the help of a community member I was able to get my graphics card working as well. When I open WoW it runs beautifully. It looks just like it did on Windows (the right resolution, etc.). I can log in, and see my characters. After I click one of my characters the loading screen will come up and get near the end (~95% maybe?). After that it just hangs and eventually crashes. I've tried the two following commands and haven't had any luck quite yet:

```
wine /home/brandon/WoW/Launcher.exe
```

```
optirun wine /home/brandon/WoW/Launcher.exe
```

I've also tried using Wow.exe instead of Launcher. Lastly I also changed my gxApi setting under /WoW/WTF/Config.WTF too as suggested in another thread:

```
SET gxApi "OpenGL"
```

Still no luck! I would greatly appreciate any help you guys can offer. Thank you very much!

[ATTACH=CONFIG]250883[/ATTACH]

---

### Post by AlwaysRemind on 2014-03-05
**SOLVED**: Sorry guys after a little more hunting I found out that the issue is because of Wow-64.exe. All I had to do is rename this file (Wow-64old.exe) and then just run Wow.exe with wine (wine /home/brandon/WoW/exe) and it was perfectly fine.

---

