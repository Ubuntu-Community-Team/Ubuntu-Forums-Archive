---
title: "[SOLVED] awn-extra applet does not work - Shows white line"
date: 2008-03-23
forum: Desktop Effects &amp; Customization
---

### Post by nidal22 on 2008-03-23
Hello,

I need help with awn-extra, the applets shows white thin line. 
I followed all the steps mentioned in 5 different threads to solve the white thin line, even I installed all dependency using Dependency Matrix from
 [http://wiki.awn-project.org/Awn_Extras:Dependency_Matrix](http://wiki.awn-project.org/Awn_Extras:Dependency_Matrix), but still the problem is not solved.

 log file for AWN, shows the error when I add stack file applets :
-------------------------------------------------------------------------------------------
$ avant-window-navigator 

Screen is composited. 
APPLET : /usr/local/lib/awn/applets/taskman.desktop 
APPLET : /home/nidal/.config/awn/applets/weather.desktop 
APPLET : /home/nidal/.config/awn/applets/Volume-Control-Applet.desktop 
APPLET : /home/nidal/.config/awn/applets/BlingSwitcher.desktop 
APPLET : /usr/lib/awn/applets/stacks.desktop 


** (awn-applet-activation:10905): WARNING **: Unable to load module /usr/lib/awn/applets/stacks/stacks_applet.py 


** (awn-applet-activation:10905): WARNING **: /usr/lib/awn/applets/stacks/stacks_applet.py: invalid ELF header 

** (awn-applet-activation:10905): WARNING **: Could not create plug 
---------------------------------------------------------------------------------------------------------------------


Any help to solve this problem is apperciated.

Nidal,

ubuntu 7.10, Dell 640m, AWN curv 

PS: I attached a snapshots for the installed file.


log files show

---

### Post by moonbeam on 2008-03-23
> **nidal22 said:**
> Hello,

I need help with awn-extra, the applets shows white thin line. 
I followed all the steps mentioned in 5 different threads to solve the white thin line, even I installed all dependency using Dependency Matrix from
 [http://wiki.awn-project.org/Awn_Extras:Dependency_Matrix](http://wiki.awn-project.org/Awn_Extras:Dependency_Matrix), but still the problem is not solved.

 log file for AWN, shows the error when I add stack file applets :
-------------------------------------------------------------------------------------------
$ avant-window-navigator 

Screen is composited. 
APPLET : /usr/local/lib/awn/applets/taskman.desktop 
APPLET : /home/nidal/.config/awn/applets/weather.desktop 
APPLET : /home/nidal/.config/awn/applets/Volume-Control-Applet.desktop 
APPLET : /home/nidal/.config/awn/applets/BlingSwitcher.desktop 
APPLET : /usr/lib/awn/applets/stacks.desktop 


** (awn-applet-activation:10905): WARNING **: Unable to load module /usr/lib/awn/applets/stacks/stacks_applet.py 


** (awn-applet-activation:10905): WARNING **: /usr/lib/awn/applets/stacks/stacks_applet.py: invalid ELF header 

** (awn-applet-activation:10905): WARNING **: Could not create plug 
---------------------------------------------------------------------------------------------------------------------


Any help to solve this problem is apperciated.

Nidal,

ubuntu 7.10, Dell 640m, AWN curv 

PS: I attached a snapshots for the installed file.


log files show


From your post I am assuming you are using curves.  I'm also assuming you're using the separate curves package and not activating the unsupported curves feature now available in trunk.

Assuming the above is true then the problem is this.  AFAIK the current awn-curves packages are based on pre awn 0.2.2 code.  With the 0.2.2+ releases backwards compatibility was broken for awn-extras (applets).  This means you cannot use awn-extras >=0.2.2 with an awn-core < 0.2.2.  And vice versa.  And looking at the list of installed applets you definitely have an awn-extras >= 0.2.2.

Actually in general you really want to match up the extras version number with the core version number.

---

### Post by nidal22 on 2008-03-23
I installed awn following the steps provided by 
[http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")

I prefer to use the applets than having the curve, Can you let me know how to match extra with core? Do you have a link?

Thanks

---

### Post by moonbeam on 2008-03-23
> **nidal22 said:**
> I installed awn following the steps provided by 
[http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")

I prefer to use the applets than having the curve, Can you let me know how to match extra with core? Do you have a link?

Thanks

Reacocard's tutorial is very good.  My suspicion is you probably have some mix of packages installed.  Best thing to do, IMO, is get rid of any traces of awn on you system, then follow that guide again.

---

### Post by nidal22 on 2008-03-23
you were right, I uninstalled AWN and I made sure there was not any trace for AWN, 

Then I reinstalled from Synpatic, and worked finally :)

Thanks moonbeam for your help,

Nidal

---

