---
title: "No cube with ATI on Gutsy"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by Martin_sensei on 2007-10-23
Hello everyone!

Please help, I had all effets working perfectly on Feisty, and I deided to make the change to Gutsy.

So, I did it in the cleanest way I could and formatted the disk and started again with a fresh install. I did the following:

1. Installed Gutsy on a formatted disk
2. Enabled the ATI restricted drivers
3. Installed xserver-xgl: ```
sudo apt-get install xserver-xgl
```
4. Added some extra compiz stuff: ```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
```

The result was, wobbly windows (which worked from the start) but no cube!  I have tried various combinations of effects in case they clashed, and I have got 4 desktops visible.

Any ideas how to get the lovely 3d cube back?

My setup is:  AMD 3200, 1 GB RAM, Maxtor 160GB, ATI X1900 XT 512MB

Regards
Martin

---

### Post by digifan on 2007-10-23
goto system ->preferences ->Advanced Desktop Effect Settings or start terminal and type ccsm after that go to desktop enable cube and rotate cube play around with the settings and voila 3d cube is back.

---

### Post by Computer Cat on 2007-10-23
In the add/remove programs manager, search for "ccsm" in "All available applications". Once the program is added, you can access it from the System -> Preferences menu, and you will find a setting under the "Desktop" section which allows you to enable the cube.

---

### Post by Martin_sensei on 2007-10-23
That simple huh!!

:) Worked fine.  Thanks for your help!! :)

---

