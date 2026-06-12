---
title: "Complete frustration - Beryl, nVidia 7900GT no worky"
date: 2007-06-13
forum: Desktop Effects &amp; Customization
---

### Post by Ma1ic3 on 2007-06-13
I tried following the instructions I found here, and then tried following the instructions I found over at Beryl's official site and both times the same thing has occurred. Beryl-manager is running in an xgl session, yet the cube does not work, and none of the settings inside the manager affect anything on the desktop what-so-ever. It still looks like the metacity theme is in control. Though when I right click on the red diamond and go Select Window Manager, beryl is selected. Also Refresh Window Manager has no effect. 

Also if I go to terminal and type beryl, I get the lovely WSOD. So, thats not encouraging. 

I will admit I am pretty fresh to Ubuntu, but seriously, I can follow directions. Let me know what information you guys need and I will be happy to provide it. Help me get this running please :)

---

### Post by Ma1ic3 on 2007-06-13
Also if someone could point me to the proper way to remove beryl so I can start again fresh and clean, I would appreciate it. Im looking around now and can't find anything concise.

---

### Post by elfstone214 on 2007-06-13
I have a 7600GT and I have followed this guide many times and always worked great

[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

---

### Post by zero244 on 2007-06-13
This should completely remove beryl from your system.
sudo rm -rf ~/.beryl* ~/.emerald* && sudo dpkg -r --force-depends beryl beryl-core beryl-manager beryl-settings emerald emerald-themes libemeraldengine0

Beryl is very cool and interesting to use if you can get it to work right.

---

