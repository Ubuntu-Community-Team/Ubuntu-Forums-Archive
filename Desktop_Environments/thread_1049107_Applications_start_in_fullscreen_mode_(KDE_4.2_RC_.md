---
title: "Applications start in fullscreen mode (KDE 4.2 RC with compiz on)"
date: 2009-01-24
forum: Desktop Environments
---

### Post by Sorai on 2009-01-24
Hello, I've got a little bit of a problem here...

Every time I start a KDE application, it starts in fullscreen mode, and well, having to manually change back every window I open into normal maximized state tends to be annoying when I'm preparing for my university exams and browsing dozens of PDFs with okular. Turning off compiz seems to work but that's not a solution since KDE desktop effects are not what I'd call a suitable replacement for compiz... The issue is, when I upgraded from Hardy to Intrepid a week ago, all seemed to work right... Then I somehow managed to corrupt the partition on which I had ubuntu and well... had to reinstall the system, which resulted in the current problem...

Anybody managed to find the solution to this problem? Google remains silent in response to my pleads for help and none of my friends uses KDE, not even mentioning the 4.2 version.

Thx for your replies in advance. Sorai ^^

---

### Post by Holy_Knight on 2009-01-29
Hi, I had the same problem and didn't find the answer ... until I get bored trying and unchecking some of the compiz plugin and I got the one who was giving me this error. This was the one:

Utilities -> Entorno de trabajo (Work Enviroment... I think) -> 
Allow Legacy on FullScreen

just uncheck that option and it's done...

I don't know if they're the exact phrases cause I have the options in Spanish but you get the idea...

Hope it works for you.

---

### Post by sspr on 2009-02-05
> **Holy_Knight said:**
> Hi, I had the same problem and didn't find the answer ... until I get bored trying and unchecking some of the compiz plugin and I got the one who was giving me this error. This was the one:

Utilities -> Entorno de trabajo (Work Enviroment... I think) -> 
Allow Legacy on FullScreen

just uncheck that option and it's done...

I don't know if they're the exact phrases cause I have the options in Spanish but you get the idea...

Hope it works for you.

I can confirm this. In The english version, you uncheck the checkbox located at:

System -> Preferences -> CompizConfig Settings Manager -> Utility -> Workarounds -> Legacy Fullscreen Support

This was also reported as a bug [https://bugs.launchpad.net/bugs/324232](https://bugs.launchpad.net/bugs/324232)

---

### Post by kag9000 on 2009-02-08
Had the same problem, thank you both for posting a solution.

---

### Post by spangaer on 2009-02-20
Solved it for me too.
(Using KDE apps in Gnome)

Thx

---

### Post by skywatcher on 2009-02-21
Hi

I have the same problem, but I don't find this on my Ubuntu 8.10 installation:

```
System -> Preferences -> CompizConfig Settings Manager -> Utility -> Workarounds -> Legacy Fullscreen Support
```

There is no "CompizConfig Settings Manager" under Preferences.

Any idea where I might find it?

Thanks.

---

### Post by NagWolf on 2009-02-26
I also sometimes battle a bit to find the path to stuff like mentioned here, dunno why, anyway, try after clicking on the "Start" button, just typing Compiz, it should show under availible options


Thanx, this solution also worked 100% for me
Cheers:popcorn:

---

### Post by skywatcher on 2009-02-26
Thanks, it worked for me, too, after I discovered that CompizConfig Settings Manager was not installed on my system!

---

### Post by simion314 on 2009-03-01
This "Utilities -> Entorno de trabajo (Work Enviroment... I think) -> 
Allow Legacy on FullScreen" worked for me in Arch linux with kde4.2 from kdemod.

---

### Post by crazy ivan on 2010-01-16
thanks! few kde4 tools I use (konsole, korganizer..) open nicely now

---

### Post by BurgerKing on 2010-05-19
Well, just found this solution for my self and this thread to late ^^

But, should this issue/bug been reported, and more precise, where?

---

