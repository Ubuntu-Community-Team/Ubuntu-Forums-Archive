---
title: "[CF] Feisty supported ATI drivers?"
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by Arsic on 2007-08-22
Hi, 
I'm new with Ubuntu. I briefly tried Ubuntu 6.10 Edgy a few months ago before going back to XP. So I decided to give Ubuntu another shot with 7.10 Feisty.

[INDENT][SIZE="1"]**Specs**
[I]AMD Athlon XP 2200+ @ 1.80GHz
ATI Radeon 9250 256MB (AGP)
256MB DDR RAM[/I][/SIZE][/INDENT]

Don't know whether I should put this in one of the other forums, or here, so I pick here.

[SIZE="5"]**-----------------------------------------------------------------------------------------------**[/SIZE]

So I want to run Compiz Fusion on Feisty, but I think I need to install the proper ATI drivers. Compiz Fusion is installed properly using the CF Installer-Updater. I had Compiz + Beryl working under Edgy and everything working properly. I understand those two projects merged back together to form Compiz Fusion, so I'm going to try that now. I followed a couple of guides here and came up with some problems.

Every time I try running **compiz --replace** or **emerald --replace** (on start up or manually), all my windows borders and title bars disappear. I have to log out with CTRL + ALT + Backspace then log back in to reset it. I can access the CompizConfig Manager and toggle the options, but none of them work. And yes, Window Decorations are on.

Can't I run Compiz Fusion unless the drivers are installed properly? I used the guide from [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) to install them and it doesn't work properly. I just get that "failed to start the X server" error after I reboot and end up having to fix it by running
```
sudo dpkg-reconfigure xserver-xorg
```
The ATI drivers or anything else for that matter, don't work. The only exception is when I select vesa, but even with that I get the no borders thing again when trying **compiz --replace**. fgrlx also doesn't seem to work.

I tried using Envy to install the drivers as well, but they won't display properly either. I get the error, "ATI's legacy driver does not support your operative system" when trying to install them. I'm guessing it's my ATI Radeon 9250 not being supported by Feisty? How can I make this work? I want Compiz Fusion and all that eye candy. It's part of the reason I switched from XP.

---

