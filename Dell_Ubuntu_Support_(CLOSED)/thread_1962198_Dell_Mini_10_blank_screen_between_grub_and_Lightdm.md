---
title: "Dell Mini 10 blank screen between grub and Lightdm U12.04"
date: 2012-04-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tulainas on 2012-04-20
Hi everyone!!

 I just installed Precise (12.04) on my dad's Dell Mini 10 netbook and everthing was going well until i found something weird.

 (1) When powered up,
 (2) grubs comes up and starts booting Precise...
 (3) screen goes purple, then blank...
 (4) a few moments after, i hear the Ubuntu login sound (still blank screen)
 (5) and... well, i can't do anything from here,
 (6) aside from pressing ctrl+alt+F1,
 (7) 'text mode'login and 
 (8) sudo 'service lightdm restart'
 (9) login again
 (10) and i'm ready to go :-)


 TRICK:

 I found that, when pressing ' ctrl+alt+F1 ' between stages (3) and (4), Precise starts and shows the Lightdm login screen as if anything had happened.


 Has this happened to you? How did you solve it?

 Thanks!!

---

### Post by wojox on 2012-04-20
Reinstall grub2?

---

### Post by pjman on 2012-04-25
I get pretty much the same thing. I've been pressing ctrl+alt+f1 and then ctrl+alt+f7 to get lightdm.

Other than this and no notification popups for the sound and brightness, I'm really like the built in 2d support for gma500 :-)

Update:

I added "acpi_backlight=vendor" (old trick from previous versions) to my grub options and now I get the notification popup when changing volume and brightness.

---

