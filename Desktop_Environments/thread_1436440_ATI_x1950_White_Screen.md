---
title: "ATI x1950 White Screen"
date: 2010-03-22
forum: Desktop Environments
---

### Post by mebunto on 2010-03-22
Hello, I've given up trying to find a solution ..... I am using gdm as I'm pretty new to Linux. When gdm starts up I get a white screen and cursor, but no display. I try alt shift f2 and restart gdm but it still comes up white screen. If I reboot then it's no better than 50:50 that I will not get another white screen. I'm updated to the hilt and the lspci entry for the display is:

[FONT=Comic Sans MS]01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV570 [Radeon X1950 Pro] [1002:7280] (rev 9a)[/FONT]

[FONT=Verdana]I can see from the various forums that this is not unique however I can't work out how to resolve the issue in my particular configuration.

Please point me in the right direction.

Thanks[/FONT]

---

### Post by mebunto on 2010-03-23
lots of people looking but no solutions ..... can anyone help please?

---

### Post by masux594 on 2010-03-23
Hi.. I've a x1950 too.. let me see.. Which release are u using? jaunty, Karmic ? .. Have u tried to install some drivers or yuo have the default one?

Sysc, A

---

### Post by mebunto on 2010-03-23
I am using Karmic and the default driver, not a vendor driver.  I do note comments that vendor supplied drivers are generally without support so I am trying not to go that route.  When it works, the default driver is fine and working at 2560x1600 resolution.

---

### Post by masux594 on 2010-03-24
Well, the proprietary driver doesen't support x1xxx series and before..So, in my pc i've installed the [radeonHd]("https://help.ubuntu.com/community/RadeonHD") ones.. In the link you'll find the step-by-step guide to insall it.. The most important thing is that your system is clear from other kind of video drivers.. Be sure that there isn't other drivers [partially] installed on it..

Sysc, A

---

### Post by mebunto on 2010-03-24
Nice one.  Will try tonight while I'm modding the wii!

---

