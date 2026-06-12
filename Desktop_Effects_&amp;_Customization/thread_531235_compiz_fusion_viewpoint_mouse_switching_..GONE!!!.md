---
title: "compiz fusion viewpoint mouse switching ..GONE?!?!?!"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by threeonethree on 2007-08-21
i was using trevernos repo and had installed compiz fusion for so much time now without problems. but today there was an update of compiz fusion the view point mouse switching was gone in compiz settings??? i can not rotate the cube with the middle mouse button now . meh it looked so cool what happend?

---

### Post by cnr437 on 2007-08-21
there is the same problem at my compiz fusion
 :confused::confused::confused::(:(

---

### Post by jsully1 on 2007-08-21
I believe it was moved to the either the compiz-fusion-plugins-unsupported or the compiz-fusion-plugins-unofficial package.  It's definitely still available.

---

### Post by threeonethree on 2007-08-23
i installed unsupported and there was mouse gesture thingy new but no mouse viewpoint switching , and i already have unofficial

---

### Post by Inxsible on 2007-08-23
there were a number of plugins that stopped working after updates including the CCSM. but Trevino's got them all working now. But you  have to do a complete uninstall of CF and then remove the config folders from /home and do a clean install again.

---

### Post by threeonethree on 2007-08-23
how ?? please im a noob :D

---

### Post by Inxsible on 2007-08-23
```
sudo apt-get remove --purge compiz* libcompizconfig*
``` This will give you a list of selections. Abort this un-install and then do

```
sudo apt-get remove compiz compiz-gnome libcompizconfig0 ....<all the package names that contain "compiz" in them from the above step>
``` This needs to be done, because I have noticed the first command does not remove all the packages, even though it selects them.

Then go to your /home folder and delete /home/.compizconfig and /home/.config/compiz.

Then enable Trevino's repos and install it again like you did last time.

---

### Post by threeonethree on 2007-08-23
sorry but this didnt help or mayb im doing somethin wrong..

i removed compiz fusion by 

 sudo apt-get remove compiz compiz-gnome libcompizconfig0 compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-fusion-plugins-unofficial compiz-fusion-plugins-unsupported compiz-plugins compizconfig-settings-manager libcompizconfig-backend-gconf python-compizconfig

then

deleted those two folders and reinstalled compiz fusion.. still NO mouse viewpoint switcher :(:(:(

---

### Post by Inxsible on 2007-08-24
> **threeonethree said:**
> sorry but this didnt help or mayb im doing somethin wrong..

i removed compiz fusion by 

 sudo apt-get remove compiz compiz-gnome libcompizconfig0 compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-fusion-plugins-unofficial compiz-fusion-plugins-unsupported compiz-plugins compizconfig-settings-manager libcompizconfig-backend-gconf python-compizconfig

then

deleted those two folders and reinstalled compiz fusion.. still NO mouse viewpoint switcher :(:(:(

Try this. you also have to delete the folder under /home/.gconf/apps/compiz and if you use kde then /home/.kconfig/apps/compiz (i think) [http://ubuntuforums.org/showthread.php?t=533201](http://ubuntuforums.org/showthread.php?t=533201)

---

### Post by silverpig on 2007-08-24
Can you switch at all? I just updated to compiz fusion on my desktop and found I had the same problem. Going into ccsm, I found that under the general options the number of desktops was set to 1. Up it to 2 or 4 or whatever you like and it might work... It did for me.

---

### Post by Shne on 2007-08-24
Even with the latest update, some of the plugins are inconfigurable with CCSM, I can only really mention the initiate cube rotation binding.
But despair not, there is another way.

use the Configuration Editor from Applications -> System Tools (right click and edit menus to add it if it's not there already).
in the configuration editor, go to /apps/compiz/plugins/rotate/allscreens/options and you can access and edit the key initiate_button to whatever mouse button you want, with any keyboard modifiers added, like <Ctrl><Alt>Button1.

---

