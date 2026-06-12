---
title: "Strange problem with the system clock~~~"
date: 2005-05-26
forum: Desktop Environments
---

### Post by piggyaugu on 2005-05-26
My system clock of Ubuntu has a strange problem. It always has 2hours's difference with my cmos clock. 2hrs beyond the real world time actually.  even when I modify it in Ubuntu, the CMOS clock is also modified and keeping the same 2hrs's difference. 

i dont have this problem with Mandriva 2005LE. Really wired. ](*,)  ](*,)

---

### Post by dave9191 on 2005-05-27
Its probably to do with the settings that you picked during install. Linux likes to have the system clock set to UTC time and then works out your local time based on that.

---

### Post by piggyaugu on 2005-05-27
[QUOTE=dave9191]Its probably to do with the settings that you picked during install. Linux likes to have the system clock set to UTC time and then works out your local time based on that.[/QUOTE]

so, is it fixable?

---

### Post by dave9191 on 2005-05-27
Just sort out your timezone settings. You can use the date command.

---

