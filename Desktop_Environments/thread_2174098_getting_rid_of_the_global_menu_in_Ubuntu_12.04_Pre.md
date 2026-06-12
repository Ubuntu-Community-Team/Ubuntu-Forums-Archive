---
title: "getting rid of the global menu in Ubuntu 12.04 Precise"
date: 2013-09-12
forum: Desktop Environments
---

### Post by Fatal Force Sam on 2013-09-12
Hey...

So recently installed Ubuntu 12.04, and this is my first use of the Global Menu/universal menu bar thing. Personally, I find it clunky and it's just not my cup of tea. No big, I can disable it and get back the traditional menu bars. I've done that, and I have that part working when the windows are NOT maximized. However, when the windows DO become maximized, this is where my problem is.

Coming from Windows, I prefer to have the minimize, maximize, and close buttons on the right hand side. Again, no problem when not maximized - I have this tweaked to my liking. The problem is, when I go to maximize a window, the stupid global menu still bites me in the ass by forcing the min/max/close options to appear in the top LEFT hand side of the screen. To me, that's just unacceptable as far as a daily use goes. I know it's not a big deal, but it's a deal breaker and I just can't for the life of me figure out how to prevent that from happening. 

Even when maximized, because I have the global menu disabled, I still have the individual menus that shows up under the top toolbar, but unfortunately the min/max/close buttons have been removed from that menu. Is there any way whatsoever to prevent that from happening? I've looked high and low, and haven't found anything. I've even gone so far as to try and script a bash script that I can use instead of using the maximize key that will maximize the window, but minus 1 pixel so as to not be truly maximized. This would be an acceptable workaround for me, but unfortunately I'm having major issues with xdotool being very inconsistent in working. It works for about the first 4 times, and then just becomes completely nonworking for that window when I try to move or resize it. Any suggestion, fixes, workarounds would be great...

~Sam

---

### Post by Frogs Hair on 2013-09-12
If you prefer a more traditional desktop there are options. ```
sudo apt-get install xfce4
```  ```
sudo apt-get install xfce4-goodies
``` or ```
sudo apt-get install gnome-session-fallback
``` Select either session at login. Of the two I prefer XFCE.

---

### Post by Fatal Force Sam on 2013-09-13
I know, I've historically avoided the Unity interface as I didn't feel it had matured enough. I decided to give it a chance though! Just trying to tweak it to my liking.

---

### Post by Frogs Hair on 2013-09-13
The title bar button behavior in Unity is hard coded .

---

### Post by Buntu Bunny on 2013-09-13
> **Frogs Hair said:**
> ... Of the two I prefer XFCE.  

+1 Xfce

---

