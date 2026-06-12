---
title: "Blank Terminal after Resolution Change"
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by towel on 2007-07-26
I ran into some problems.  I recently switched my resolution from 1024x768 to  1280x768.  I did this through the command > sudo nvidia-settings

Everything seems to be working fine except now whenever I open a terminal window I get a blank screen.  Nothing inside and on top of that any applications I open has no corner boxes (Minimize, Maximize, Close) and I can't move them anywhere on the screen.  Where they open is where they stay.


I'm very confused and have been searching the forums

I tried
> dpkg-reconfigure x-server-xorg

but, wasn't able to fix it.  I also tried to change the resolution back but, the problem still occurs.  Can anyone shed some light here lol?

Hardware:  LG L194WT / Geforce FX5800 Ultra

Thanks.

---

### Post by towel on 2007-07-26
Opps I think I posted in the wrong section.  Can someone move this post?

---

### Post by towel on 2007-07-26
Nevermind managed to fix it.  I uninstalled / reinstalled nvidia-settings and then played with the xorg config.

---

### Post by mikex on 2007-08-13
> **towel said:**
> Nevermind managed to fix it.  I uninstalled / reinstalled nvidia-settings and then played with the xorg config.


Could you post what you played with to fix it, I have the same problem but I don't know the nagic text to type in the xorg.config file. Thanks.

---

