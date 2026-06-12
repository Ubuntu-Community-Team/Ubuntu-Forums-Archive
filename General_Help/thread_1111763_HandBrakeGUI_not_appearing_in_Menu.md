---
title: "HandBrakeGUI not appearing in Menu?"
date: 2009-03-31
forum: General Help
---

### Post by Mic_Droz on 2009-03-31
Hey guys, 

I've downloaded the HandBrake 0.9.3 deb, from the Handbrake website, and Have successfully installed it... but I can't find it in my menu...

I remember that when i was testing earlier versions compiled from svn, it had an icon in the menu, and then when it stopped working, i removed it somehow... But now when I reinstall it, it won't appear. 

I realise that this could be seen as simply HandBrake related, and someone will tell me to bugger off to the HandBrake Forums or something, but... I think this is some Linux/ubuntu thing that I've somehow managed to destroy, and therefore someone out there will be able to point me in the right direction...

Cheers In Advance!
Droz

---

### Post by jmszr on 2009-03-31
Mic_Droz,
          You might try System > Preferences > Main Menu > Click Sound and Video on the left hand side under Menus: > and then make sure Handbrake is checked under Items:.

---

### Post by Mic_Droz on 2009-04-07
have tried that, it doesn't exist there either...

---

### Post by mb_webguy on 2009-04-07
Well, you could just create it.  On my system, at least, the icon is located at "/usr/share/icons/hicolor/128x128/apps/hb-icon.png", and the command should be "ghb %f".

Of course, I installed HandBrake from the [HandBrake PPA]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa"), so YMMV.

---

