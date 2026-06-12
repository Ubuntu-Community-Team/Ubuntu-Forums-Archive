---
title: "Odd pointer/custor image stuck on screen...."
date: 2005-02-20
forum: Desktop Environments
---

### Post by joobuntjoo on 2005-02-20
Hiya, fairly new to Ubuntu (but ok with most linux stuff), and have an odd one wasn't sure how to explain.

Firstly I have just installed Ubuntu (debian 1:3:3.4-9ubuntu5)  on a Fujitsu laptop, and running gnome.

During the final bootup part (past the login screen), a big black diagonal cross/pointer appears in the middle of the screen (kinda like the old mouse pointer with no high res desktop). This is different to the normal smaller mouse pointer which moves fine according to mouse/touchpad movements.

The big black pointer, is just stuck bang in the middle of the screen though and is "above" anything, ie it will be in front of any new window or anything. Eventually after moving various windows about "over" it, seems to somehow eventually trick it into vanishing?

Sorry, not a very good explanation, and wouldn't be able to do a screeny (was going to try, but by the time I get into using an app it just about is gone, so too late and not sure it would capture it anyway.

So any ideas on that hazy description? How to stop this erm huge diagonal cross pointer thingy from appearing in the middle of the screen, in front of apps etc? (One thing I was wondering was the fact the lappy has a touchpad and mouse mad it think it should have 2 mouse pointers or something, but tried it without the mouse and its the same).

---

### Post by kassetra on 2005-02-20
Ok, here is how you fix that problem:
 
 1. Open a terminal (Applications->System Tools->Terminal)
 2. Type this line:
  ```
sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4_backup
``` 
 and press enter.  (you'll have to enter your password)
 3. Now type this line:
  ```
sudo gedit /etc/X11/XF86Config-4
``` 
 4. When the text editor pops up, scoll down to 
 ```
Section "Device"
```
 5. Add this line under the Section "Device" line:
  ```
Option "HWCursor" "false"
``` 
 6. Save & Close the file.
 7. Reboot your machine (just logging out will not restart X).

---

### Post by joobuntjoo on 2005-02-21
Ah superb :), thanks muchly! V.impressed so far with ubuntu on the laptop, seems to have pretty much everything needed installed straight away for it, unlike nearly every other distro with this lappy.

---

