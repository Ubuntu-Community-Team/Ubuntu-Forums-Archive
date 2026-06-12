---
title: "Gutsy bug while resizing windows."
date: 2008-03-06
forum: Desktop Environments
---

### Post by nikiu on 2008-03-06
I have Gutsy, clean install, not upgrade. I am using a Dell Inspiron 8600. When I try to resize windows (with visual effects enabled under Compiz), my CPU starts to work with 100% capacity and the laptop seems to hang up. I have to struggle to disable the visual effects to return to normal condition and then I can enable again the visual effects without problem. This happens always, in every occasion that I try to resize a window. My GFX card is ATI Radeon 9600 (128 MB RAM) and the driver I am using is the fglrx one.

Any suggestions please?

---

### Post by zerofx on 2008-03-16
I'm having the same problem. It and the effects run fine until I try to resize a window. Then it's a slow as a snail. But it's only until I attempt to resize a window.

---

### Post by memstat on 2008-03-26
i myself have the same problem...i am assuming it might be an issue with ati drivers.....i have a radeon 9800xt and the same thing happens to me, i have ctrl+alt+bs to make it stop and try not to resize any windows.  after awhile i just turned window resizing off and used a new workspace for every app.......we need help....

---

### Post by nikiu on 2008-03-26
With the Feisty Fawn version, it used to go fine on Beryl. I didn't have any problem and I used to have the ATI drivers installed. Probably this is some bug under Compiz but I am a newbie on Linux.

---

### Post by Kralizec on 2008-03-27
I have the same problem and I'm tired of dealing with it, so I'm looking for a solution. But, the easiest and least obtrusive way of fixing the problem when it happens is to hit alt+f2 to open a Run Application dialog and type **killall compiz.real; compiz**. That will kill the compiz effects and immediately restart them. Hope this helps you guys, but I'd really like to find a fix.

---

### Post by Kralizec on 2008-03-27
I found a workaround. In your compiz settings manager (alt+f2 then "ccsm" or System->Preferences->Advanced Desktop Effects Settings), go all the way to the bottom to "Resize Windows" and select for "Default Resize Mode" either Stretch or Normal. I found that with either Outline or Rectangle the problem would occur.

EDIT: This solution confirmed in this thread: [http://ubuntuforums.org/showthread.php?t=552372]("http://ubuntuforums.org/showthread.php?t=552372")

---

### Post by nikiu on 2008-03-27
Can't wait to test it but I am getting back to my laptop after two weeks. Can anyone confirm if this works? (Even if this is confirmed at the other post)

---

### Post by nikiu on 2008-04-28
Yeah it works.

I installed Hardy as well (first upgraded from Gutsy then Clean Install) and the problem disappeared.

Thnx man.

---

