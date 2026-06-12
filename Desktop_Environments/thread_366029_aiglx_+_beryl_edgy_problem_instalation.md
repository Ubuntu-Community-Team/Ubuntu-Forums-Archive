---
title: "aiglx + beryl edgy problem instalation"
date: 2007-02-20
forum: Desktop Environments
---

### Post by _deXter on 2007-02-20
Hello!

I'm trying to install aiglx + beryl at my Ubuntu Edgy.
I've a radeon 9250, but I cant get aceleration 3d.
My drivers are opensource "ati".
I tried to activate aceleration 3d:

```
#apt-get install driconf
$driconf
```

But when I type: driconf, I get this: 

```
 Driver "r200" is not installed or does not support configuration.
/usr/lib/python2.4/site-packages/driconf_complexui.py:843: DeprecationWarning: 
  "priv", self.configTree.saveConfig, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:846: DeprecationWarning: 
  "priv", self.configTree.reloadConfig, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:847: DeprecationWarning: 
  self.toolbar.append_space()
/usr/lib/python2.4/site-packages/driconf_complexui.py:850: DeprecationWarning: 
  "priv", self.configTree.newItem, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:853: DeprecationWarning: 
  "priv", self.configTree.removeItem, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:856: DeprecationWarning: 
  "priv", self.configTree.moveUp, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:859: DeprecationWarning: 
  "priv", self.configTree.moveDown, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:862: DeprecationWarning: 
  "priv", self.configTree.properties, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:863: DeprecationWarning: 
  self.toolbar.append_space()
/usr/lib/python2.4/site-packages/driconf_complexui.py:872: DeprecationWarning: 
  self.aboutHandler, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:873: DeprecationWarning: 
  self.toolbar.append_space()
/usr/lib/python2.4/site-packages/driconf_complexui.py:876: DeprecationWarning: 
  self.exitHandler, None, -1)
```

I dont no what to do.

Thanks.

---

### Post by _deXter on 2007-02-20
Anyone has an ideia how to solve this problem?

Thanks.

---

### Post by _deXter on 2007-02-21
)'m seeing that this problem is dificult to solve... :\

---

### Post by john.nicholls on 2007-02-21
I have the ATI 9250, and installed Beryl with AIGLX and the Ubuntu Radeon driver on Edgy following the instructions for that combination on the Beryl website. I didn't need to install driconf.

---

### Post by reallxry on 2007-02-22
i'm newbie on linux.

my comp is **ubuntu edgy** on *athlon2500/radeon9200SE*
Here is really simple working beryl method.


firstly remove flgrx and needed file install.
```
sudo apt-get remove xorg-driver-fglrx; sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
```

secondary open xorg.conf by root
```
sudo nano /etc/X11/xorg.conf
```

add these option in xorg.conf
```
Section "Device"
&#12288;Option&#12288; "XAANoOffscreenPixmaps"
EndSection

Section "server layout"
 Option "AIGLX" "true"
 Identifier "Default Layout"
 Screen "Default Screen"
EndSection

Section "Extensions"
&#12288;Option&#12288;"Composite"&#12288;"Enable"
EndSection
```
[COLOR="Red"]_attention: "space" must be "tab space"_[/COLOR]


now your radeon vendor will be **[SIZE="3"]SGI[/SIZE]** and 3D working will be "**[SIZE="3"]yes[/SIZE]**"
check vendor command
```
glxinfo | grep vendor
```
check direct command
```
glxinfo | grep direct
```

now driver is ready to use beryl and AIGLX.




next, install beryl

firstly add repositry
```
sudo nano /etx/apt/sources.list
```

add these line in sorces.list
```
deb http://ubuntu.beryl-project.org/ edgy main
deb-src http://ubuntu.beryl-project.org/ edgy main
```

use these command.
```
sudo apt-get update
```
```
sudo apt-get install beryl beryl-plugins-data emerald-themes 
```




***[SIZE="3"]now beryl successfuly installed on your ubuntu.[/SIZE]***



Let's start beryl !!
```
sudo beryl-manager
```







if u want autostart beryl,
go "system/preference/session"
push "add" and type ***beryl-manager*** in "autostart apprication"

---

