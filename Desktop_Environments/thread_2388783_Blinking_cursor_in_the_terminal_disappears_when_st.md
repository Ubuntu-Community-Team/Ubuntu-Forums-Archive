---
title: "Blinking cursor in the terminal disappears when starting ATOK software"
date: 2018-04-07
forum: Desktop Environments
---

### Post by LastStarDust on 2018-04-07
Hello!
I have just moved to Japan and I bought the "ATOK X3 for Linux" software to properly input Japanese characters. 
It is a marvelous piece of software that I was already using in Windows and I paid it a premium but I think it was worth the money.
Anyway, I managed to install it on Ubuntu 17.10, even if it is quite an old version. I followed the two guides below:
#1 [Japanese]("http://r03.nurse.medic.mie-u.ac.jp/Ubuntu/UbuntuXenial.html#sec12") [English]("https://translate.google.com/translate?hl=&sl=auto&tl=en&u=http%3A%2F%2Fr03.nurse.medic.mie-u.ac.jp%2FUbuntu%2FUbuntuXenial.html%23sec12&sandbox=1")
#2 [Japanese]("https://sicklylife.jp/ubuntu/1404/settings.html#atok_in") [English]("https://translate.google.com/translate?hl=&sl=auto&tl=en&u=https%3A%2F%2Fsicklylife.jp%2Fubuntu%2F1404%2Fsettings.html%23atok_in")
Now everything is working except for a little but annoying thing, apparently completely unrelated to the software.
The thing is that in the gnome-terminal the blinking cursor that shows the position is gone. 
As soon as the ATOK software is started the cursor disappears, just like as the command ```
setterm -cursor off
``` was issued.
Again I am not talking about the mouse cursor. Only the blinking cursor in the terminal.
Do you know how could I bring it back? Typing anything in the terminal has become a real pain in the back!
Thank you

(maybe) relevant info:
[LIST]
[*]```
$ uname -a
Linux zion 4.13.0-38-generic #43-Ubuntu SMP Wed Mar 14 15:20:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```
[*]Lenovo Carbon X1 Gen6
[*]ATOK X3 for Linux Tech Ver.20
[*]GNOME Shell 3.26.2 (Adapta-Nokto theme)
[/LIST]

---

### Post by LastStarDust on 2018-04-17
Really, no one has any clue?

---

### Post by kerry_s on 2018-04-17
did you check the terminal profile?
[ATTACH=CONFIG]279326[/ATTACH]

---

### Post by LastStarDust on 2018-04-20
Yes, I have deleted all the profiles just in case.

---

### Post by kerry_s on 2018-04-20
still didn't come back?
it's only after you launch the software from terminal? or you launch the software then go into terminal?

does the same thing happen if you launch the software from the alt+f2 run command?

---

### Post by LastStarDust on 2018-04-22
> **kerry_s said:**
> still didn't come back?
it's only after you launch the software from terminal? or you launch the software then go into terminal?

does the same thing happen if you launch the software from the alt+f2 run command?

The application is started with the following script:
```
/opt/atokx3/bin/atokx3start.sh
```
I usually run it at startup as an autostart application. If I don't run it the blinking cursor is showing correctly at startup.
If I run that script (in the terminal or with alt+F2 there is no difference), the blinking cursor doesn't disappear instantly. But as soon as I change input method and start writing in Japanese the blinking cursor disappear for all the remaining session. The only way to make it reappear is to reboot.

---

### Post by kerry_s on 2018-04-22
i think you should report it as a bug against ATOK X3 cause it's breaking your term, it's obviously the software at fault.

---

### Post by LastStarDust on 2018-04-26
The problem is that the software has already reached end of line (and of support)

---

