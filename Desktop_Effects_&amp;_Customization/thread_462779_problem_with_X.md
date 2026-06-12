---
title: "problem with X"
date: 2007-06-03
forum: Desktop Effects &amp; Customization
---

### Post by chinayem on 2007-06-03
first ,i wanna to change the refresh rate ,found the xorg.conf,then i changed the HorizSync  and   VertRefresh 
like this:
Section "Monitor"
   Identifier   "SyncMaster 788DF"
   HorizSync       30-55
   VertRefresh   50-120
   Option            "DPMS"
EndSection

But now i can't start  X window and i can  login with text !

anyone can help me?
thank you

---

### Post by coolzgeek on 2007-06-03
So go to command line and type
[PHP]sudo apt-get remove xorg
sudo apt-get install xorg[/PHP]
restart your computer and you can log in to X.
Then, I know how to reconfigure resolution on KDE like this.
Go to System Settings>Monitor & Display>Hardware. Click Administrator mode on the right bottom and then click settings for monitor 1 and 2. You will see a list of resolution. Click on the desired one and apply.

---

