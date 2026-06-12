---
title: "chnage gnome shell to gdm mode"
date: 2013-04-20
forum: Desktop Environments
---

### Post by gnugen on 2013-04-20
Hello,
I am a newbie to ubuntu and its variants. I recently installed GNOME Shell through the ubuntu software centre and midway through the download, a window apperared asking me to choose lightdm or gdm. I chose lightdm, but when I try to login to gnome, I do not see a panel at the top. However, gnome classic works. I later on realised that I am using gdm as I use lubuntu. I tried uninstalling and reinstalling gnome shell hoping that the window would appear again so I can choose gdm but the window did not appear and GNOME still refuses to work. Is their a way to change GNOME to gdm mode? 

Sorry if this does not make sense but I am a newbie so I do not really understand lightdm and gdm.

---

### Post by markbl on 2013-04-21
GNOME Shell should work fine with lightdm or gdm. It should not make any difference. You can swap between gdm and lightdm at any time by running:
```

sudo dpkg-reconfigure gdm

```

It will show the current setting and prompt to change it.

If you are missing the top panel then something else is wrong though.

---

### Post by gnugen on 2013-04-21
Thanks, it works now. I also had to use gnome tweak tool. However, its not using the theme that I set. Do you know why? If you do not know its alright as well because I can manage this. Thank you again for your help.

---

### Post by markbl on 2013-04-21
Oh, a theme issue. I should have thought of that. There are heaps of problems with 3rd party themes and in particular plenty of theme compatibility issues across the various gnome shell versions 3.2 to 3.8 etc. I stick to the default Ubuntu ambiance theme because I think it looks great and I know it won't have compatibility problems.

---

### Post by Baldrick_NZ on 2013-04-22
It also depends on what shell extensions you have installed, too. I've found on my i386 puters I can't use the 'appindicator support' extension because it crashes the desktop requiring a reboot, and when restarted, it defaults to the standard settings and theme. Only resetting them in gnome tweak tool restores them to my preferred settings. No such issues with 64bit.

---

### Post by gnugen on 2013-04-23
Thanks Baldrick_NZ. I have realised the theme I was trying to use does not have gnome shell support(although it works fine in Cinnamon and Unity). 

Also, I will only upgarde to 13.04 if there is some cool new feature you cannot get for 12.10 as they have cut down the support time for 13.04 to 9 months.

---

