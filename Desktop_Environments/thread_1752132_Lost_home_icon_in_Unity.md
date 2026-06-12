---
title: "Lost home icon in Unity"
date: 2011-05-07
forum: Desktop Environments
---

### Post by ffeingol on 2011-05-07
Somehow I managed to loose my 'Home' icon in the Unity launcher.  I can launch nautilus but it comes up as "file manager" not "home".  Any thoughts on getting it back?

TIA

---

### Post by coffeecat on 2011-05-07
I'm sure there's an easier way, but try this. Right-click on the desktop and choose "Create Launcher". In the first two fields, you need:

Name: Home Folder
Command: nautilus /home/*yourusername*

Substitute your account name for *yourusername*. At the moment the icon will be showing as the nautilus shell. If you want the proper folder icon, click on the icon field and navigate to /usr/share/icons/ubuntu-mono-dark/places/64/ and choose the folder_home.svg icon. Now OK the "Create Launcher" window and a launcher with the correct name and icon will appear on your desktop. Now simply drag it into the dock. You can now delete the desktop launcher.

---

### Post by ffeingol on 2011-05-07
@coffeecat,

Sorry, but nope.  It added to the Unity launcher but the extra items I have applied (when you right click) don't show up (things I have modified in nautilus-home.desktop).

---

### Post by ffeingol on 2011-05-07
unity --reset-icons did the trick.

---

### Post by coffeecat on 2011-05-07
> **ffeingol said:**
> unity --reset-icons did the trick.

Excellent! My apologies for temporarily forgetting the unity --reset command. Advancing years, you see. I get forgetful. :(

Er - what was I saying?

:wink:

Good luck!

---

