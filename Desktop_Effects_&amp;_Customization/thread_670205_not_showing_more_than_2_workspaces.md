---
title: "not showing more than 2 workspaces"
date: 2008-01-17
forum: Desktop Effects &amp; Customization
---

### Post by grebarton on 2008-01-17
I have recently installed a new graphics card to get visual effects working but now my bottom menu bar will not show more than 2 available workspaces but they were available before the install.

How can I make it so I can use 4 workspaces again?

---

### Post by arvindenrique on 2008-01-17
right click on the workspace--->preference and change the workspace to ur need. to get visual effects with cube , u should have 4 workspace



PLEASE SAY THANKS by clicking thanks button

---

### Post by grebarton on 2008-01-17
I have already had it changed to 4 workspaces as I did before i got the new card. But it simply won't display them all or scroll through any but the first 2 when I use the scroll wheel.

Any other ideas?

---

### Post by arvindenrique on 2008-01-17
delete the panel and create a new panel and select add to panel--->workspace switcher and then follow the last post.

---

### Post by grebarton on 2008-01-17
Sorry its still not working tried it various ways and still only shows 2 workspaces with compiz running, when i switch compiz off it shows the 4 workspaces again.

---

### Post by sisco311 on 2008-01-17
do you have compizconfig-settings-manager installed?
if not install it from a terminal:
```
sudo aptitude install compizconfig-settings-manager
```run compizconfig-settings-manager:
```
ccsm
```(or from Applications -> Setting -> Advenced Desktop Effect Setting???)

go to the General Options -> Desktop Size tab and set Number of Desktops to 4

---

### Post by grebarton on 2008-01-17
I do appear to have the settings manager installe dbut when i try to run it I get this:

grebarton@grebarton-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
grebarton@grebarton-desktop:~$ 

Thanks for all your help so far.

Any idea why its not running?

---

### Post by sisco311 on 2008-01-17
i hope [this thread]("http://ubuntuforums.org/archive/index.php/t-573297.html") will help you.

---

### Post by Jake90 on 2008-01-20
Try going into system>preferences>advanced desktop effect settings click on general options then click the desktop size tab.change the horizontal virtual size to however many workspaces you want. Hope this helps

---

