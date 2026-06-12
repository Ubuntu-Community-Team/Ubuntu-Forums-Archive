---
title: "beryl on ati xpress 200"
date: 2007-05-22
forum: Desktop Effects &amp; Customization
---

### Post by hhpeter on 2007-05-22
hi everybody
I have recently installed ubuntu feisty fawn on my windoze pc ......so I'm a completly newbe to linux
I read and read and read and tried to install beryl .....once I actually installed it but it wasn't working like I had the red diamond in the tray but I could not make it to work so I tried something else until I fu**** up my pc and I need to reinstall the ubuntu again....
my question : is there somebody who has beryl with ubuntu feisty fawn on a ati radeon xpress 200  working? please help ...

---

### Post by Melcar on 2007-05-23
Managed to get Beryl working on my Compaq laptop running a 200M chip.  Feisty is being especially problematic with ATI drivers (for me at least) so it took some time to get it right.  I basically installed the drivers by way of the repos. and installed Beryl with a separate XGL session.  Just remember to lock your beryl-core version to 0.2.0.

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

---

### Post by SanjoEel on 2007-05-29
I have it working on mine with an ATI 200 series card. You have to run it under xgl. The main things to remember are that you must disable the universe repos before installing it, and don't install any updates for Beryl. Here is a link to the tutorial I used to install Beryl. [http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty]("http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty")Read through the whole thread as there are some bits of useful info in there Follow the instructions exactly and do it from a fresh feisty install and you should be good to go. Again, make sure universe is disabled. If you want to enable universe later make sure you DO NOT install any of the Beryl updates as they will break it for sure, there is no XGL support yet. Also, you will notice a bug when trying to log out of an XGL session, there won't be any restart or shutdown buttons in the logout menu, AND when you DO logout to restart X it will probably crash. Fix the missing buttons by using the bugfix in the tutorial, it works. If you just want to logout and restart X from XGL, don't use the logout button, use ctrl + alt + backspace to logout instead and it shouldn't crash on you. The restart and shutdown buttons will work, though. Good luck, if you have any problems post them. I'm a noob too but I got it working and "stable" hahaha but I'll help any way I can. Beryl rocks and no Linux system should be without it! :D 
Oh yeah, this tuorial is great too. [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL") Pay special attention to the part "Downgrading Beryl-core" This is important. Make sure to add that to your /etc/apt/preferences file.

---

