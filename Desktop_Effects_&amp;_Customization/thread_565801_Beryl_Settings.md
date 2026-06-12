---
title: "Beryl Settings"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by ep3w on 2007-10-02
I was messing with some of the beryl settings in the drop down menu from the icon and accidently change the rendering from automatic to xgl (i think).  Now when I boot its just all rectangles.  I am assuming I need to edit my xorg.conf, but I am not quite sure what I need to change.  Can I easily edit it from a live CD or do I need to do it in recovery mode? Any suggestion on what exactly i need to change, i don't want to change the wrong thing, and the easiest way to edit it? Thanks!

---

### Post by haden9 on 2007-10-03
You can try accessing the computer in Safe Mode, then uninstalling Beryl.

sudo apt-get remove beryl beryl-manager beryl-core

That should get you back your desktop to normal, then its just to reinstall beryl again and play with the settings :)

---

### Post by FuturePilot on 2007-10-03
Remove the .beryl-managerrc file in your home folder. It will reset the Beryl Manager setting to the default. No need to edit your xorg.conf
By the way it's a hidden file so open your home folder and press Ctrl+H to view hidden files.

---

