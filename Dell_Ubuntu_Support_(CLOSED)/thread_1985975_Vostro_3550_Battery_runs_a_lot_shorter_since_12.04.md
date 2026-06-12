---
title: "Vostro 3550: Battery runs a lot shorter since 12.04"
date: 2012-05-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by alex-s77 on 2012-05-24
Hello

I have 12.04 installed (upgraded from 11.10) on my Vostro 3550 (8 GB RAM, 180 GB SSD, no normal HD). I use Gnome 3 (ie. no Unity).

Since "recently" (I think since the upgrade to 12.04), **I find that the battery doesn't last as long anymore**, as it used to "back then" (ie. in 11.10 times). According to the battery widget in Gnome, the battery is 85% full and has 1:41 hours to go; [FONT="Courier New"]powertop[/FONT] shows:


Ich setze auf meinem Dell Vostro 3550 (8 GB RAM, 180 GB SSD - keine "normale" HD) Ubuntu 12.04 64bit mit Gnome 3 (kein Unity) ein; hab's von 11.10 aktualisiert. Ich meine, das sich seit dem Update die Laufzeit des Akkus massiv reduziert hat.

```
Der Akku meldet eine Entladungsrate von 29.3 W
Die verbleibende Zeit beträgt schätzungsweise 85 Minuten
```

(Ie. Discharging with 29.3 Watts, and 85 minutes to go)

The system has 2 graphic cards built in:

```
ag@ubuntu-nb:~$ sudo lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Series]
```

In 11.10 times, I deactivated the discrete AMD graphics card, based on the information found on [https://help.ubuntu.com/community/HybridGraphic](https://help.ubuntu.com/community/HybridGraphic) . The card is still turned off:

```
ag@ubuntu-nb:~$ sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0
```

What could be done, to make the battery last longer?

Thanks,
Alexander

---

