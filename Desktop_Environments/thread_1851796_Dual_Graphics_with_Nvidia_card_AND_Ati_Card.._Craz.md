---
title: "Dual Graphics with Nvidia card AND Ati Card.. Crazy I know"
date: 2011-09-29
forum: Desktop Environments
---

### Post by Hexxus on 2011-09-29
Hello there,

By strange circumstances here is my dillema, I'm switching over from Windows 7.


I have 3 monitors at home  - 2 graphics cards.

1. Nvidia 7900GS 2X DVI - using only one for my middle monitor.

2. ATI Radeon 4550 - 1DVI 1VGA - they power my outer two monitors.


Is it possible to make this work?  Believe it or not I was able to very easily in Windows 7. In Ubuntu I downloaded the prop. Nvidia Drivers and had my middle monitor. Rebooted and didnt have the outer two. (They showed up when I was booting up and showed the Ubuntu dots)

So then I installed the Ati drivers, rebooted and still no outer two monitors but strangely... I had the middle. When I tried to launch the ATI catalyst center it stated that it was missing drivers or they were improperly installed.


This could be common knowledge like it was with Windows pre 7, but does Ubuntu support having both Nvidia and ATI cards in use at the same time?


Thank you all for you help, I did a bunch of google searches but it didn't get me anywhere.

---

### Post by 3Miro on 2011-09-30
The proprietary Nvidia drivers have quite a mind of their own. They make some changes to the system and are hence incompatible with any other video cards. Ultimately Nvidia doesn't play nice with other cards, its their way or no way. The ATI drivers may be more friendly, but ultimately they will not work either.

Your only chance of getting both cards to work is to use the default FOSS drivers for both cards. You may have to manually edit the Xorg.conf settings.

---

