---
title: "clicking Places &gt; Desktop raises VLC"
date: 2010-12-22
forum: Desktop Environments
---

### Post by emwaiz on 2010-12-22
Hi everyone! I'm having problem with trying to click shortcuts in my **Places** menu! When I click **Places > Home** or **Places > Desktop** or **Places > Video** and etc ... It will raise VLC media player! It has been 3 weeks already and it's really bugging me. I thought, updating/upgrading the system, would cut it, but it didn't! So, when I want to explore the Home environment, I have to click **Places > Computer**! Please help me with this bug!

---

### Post by gadolinio on 2010-12-22
Weird thing... What happens if you uninstall VLC? Does it complain about not finding it, or does it open the folder it shoud? What about reinstalling?

---

### Post by Frogs Hair on 2010-12-22
From the places menu open the file browser from the computer icon and navigate to the home folder . Right click on any folder , select open with another application , from the menu select file browser and make sure the remember this application box is checked.

If you can't get into the file browser from the computer icon right click on the desktop and create a new folder
and do the same thing and  test the places menu . remove the new folder if you wish.

---

### Post by hariks0 on 2010-12-22
It is because you have set the default program to open inodes/directories to VLC instead of Nautilis or Dolphin.

GUI 

Change under 'Session control' in 'Ubuntu Tweak'
Delete nautilus and type in pcmanfm or another file manager such as thunar
Apply
Quit ubuntu-tweak
Reboot

OR

TERMINAL

```
gksu gedit /usr/share/applications/nautilus-folder-*handler.desktop
```
Then replace 'nautilus --no-desktop %U' to whatever you like. Example: pcmanfm %U

---

### Post by plumper on 2010-12-23
Thanks for the help! I had the same problem!     :D

---

### Post by dgvigil on 2011-01-01
> **Frogs Hair said:**
> If you can't get into the file browser from the computer icon right click on the desktop and create a new folder
and do the same thing and  test the places menu . remove the new folder if you wish.


This is a great simple solution if any software is opening folders.

---

### Post by okkie on 2011-01-10
thanks a lot it also solved my problem

---

### Post by emwaiz on 2011-04-12
> **hariks0 said:**
> It is because you have set the default program to open inodes/directories to VLC instead of Nautilis or Dolphin.

GUI 

Change under 'Session control' in 'Ubuntu Tweak'
Delete nautilus and type in pcmanfm or another file manager such as thunar
Apply
Quit ubuntu-tweak
Reboot

OR

TERMINAL

```
gksu gedit /usr/share/applications/nautilus-folder-*handler.desktop
```
Then replace 'nautilus --no-desktop %U' to whatever you like. Example: pcmanfm %U
Thank you! It solved my problem!

---

