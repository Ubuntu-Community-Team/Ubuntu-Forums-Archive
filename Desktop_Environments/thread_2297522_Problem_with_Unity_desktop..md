---
title: "Problem with Unity desktop."
date: 2015-10-04
forum: Desktop Environments
---

### Post by irv on 2015-10-04
I am posting this under desktops because I believe the problem is in the Unity desktop. I am using Ubuntu 14.04 with Unity.
I have a laptop on the sound system at the chapel that I use to do all the recordings. Today I booted the system and all it will do is come to a desktop with no launcher or menus just a plain desktop with just the wallpaper. You can't do anything but right mouse click and change desktop images. The only thing I could do was power it off and change to Gnome desktop and then everything worked.
I have another user setup so I can change to that user and boot into the unity desktop with no problem.
This problem just exist with this one user and only in Unity.
So far the only thing I tried was to reload the Unity desktop while logged onto it with this problem user in Gnome, but this did not fix the problem. Also tried booting into recovery and ran fix all installed apps. 
Any idea what to try.  I am thinking it might be a corrupt file for desktop configuration, but not sure. 
The laptop is at a different location so what ever is posted here will have to be tried later when I am in front of this computer.
Thanks

---

### Post by deadflowr on 2015-10-04
Sounds like unity and compiz went belly up, at least for a moment.
Possible fix is to try to get a terminal open with ctrl + alt + T
and run:
```
dconf reset -f /org/compiz/
```
then run
```
setsid unity
```
Then I'd logout and back in again to see if it sticks.

referenced from here with other possible solutions:
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

see if it helps

---

### Post by irv on 2015-10-05
I will give this a try the next time I get there which should be tomorrow. I will let you know if that fixes it.
EDIT: Okay, I went down and tried the "dconf", but at first it didn't work. I found I a plugin "opengl" was corrupt or not installed. After reinstalling it and running the dconf reset and then do a setsid unity, rebooting everything is back working again. I had to boot into the Gnome desktop to do all of this because with  X11 not running and just jumping to Ctrl Alt F1 I couldn't I had trouble trying to run the fix.
Thanks for the help and I will mark solved.

---

