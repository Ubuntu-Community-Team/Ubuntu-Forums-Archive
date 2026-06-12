---
title: "Xubuntu Hell"
date: 2007-06-12
forum: Desktop Environments
---

### Post by ErusGuleilmus on 2007-06-12
Well, maybe hell is a little bit of an over exaggeration, but it comes damn close. Anyway, after downloading Beryl and attempting to run it, it failed. I wouldn't have come to this forum just because of that though. I guess when I ran Beryl, some corruption occurred. All my windows no longer have borders and cannot be minimized. Also, on start up, my icons are partly under the apps. bar. I have no inkling as how to fix this, so any assistance would of course be greatly appreciated.

---

### Post by band-aid on 2007-06-12
Try to alt+click on the windows and move them around, if they wiggle when you do then beryl is stilll running and thats why you don't have borders, there are some simple changes that you have to make in your xorg.conf ( can't remember what they are). If they don't wiggle you just need to set your default window manager back to metacity (not sure how to do this either, look in your system menu (if your using xfce).

---

### Post by ErusGuleilmus on 2007-06-12
Beryl is not running, and I have no way (that I know of) to switch back to default. If some one could post how to fix the xorg files, or at least get the windows working right, that would be great.

---

### Post by ErusGuleilmus on 2007-06-12
This issue has been resolved. I installed Metacity using sudo apt-get install, then ran metacity using terminal. One more question though, does Xubuntu by default use metacity, and if not, what does it use by default?

---

### Post by Sunflower1970 on 2007-06-12
> **ErusGuleilmus said:**
> This issue has been resolved. I installed Metacity using sudo apt-get install, then ran metacity using terminal. One more question though, does Xubuntu by default use metacity, and if not, what does it use by default?


No, Xubuntu doesn't use Metacity by default. It uses xfwm4 as the windows manager.

If, when you boot up Xubuntu for the first time, and don't see the WM, you can add it to the start menu (or is it sessions...) to make sure it always begins. I had this very problem, in one instance of Ubuntu, and one of Xubuntu. Once the WM was added to the start or sessions menu, I've not had a problem since.

---

