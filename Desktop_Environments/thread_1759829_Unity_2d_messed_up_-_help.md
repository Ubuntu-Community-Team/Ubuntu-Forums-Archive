---
title: "Unity 2d messed up - help"
date: 2011-05-16
forum: Desktop Environments
---

### Post by rereradu on 2011-05-16
I updated to 11.04 but Unity was slowing down my computer significantly so I installed Unity 2D, which worked like a charm. Until I went around messing with it pretty bad. 
What I did:
I tried to change the launcher icons, so I went and edited  Launcher.qml, LauncherList.qml and LauncherItem.qml following some instructions I found [here]("http://bhou.wordpress.com/2011/05/06/change-the-icon-size-in-unity-2d-launcher/"). Reckless enough, I did not make a back-up of these files (stupid!). After restarting Unity 2d, the launcher showed completly blank. I tried removing and reinstalling Unity 2d (from Ubuntu Classic session) but when logging in to Unity 2d session again, the launcher was still showing blank. So then I made another mistake... I removed the usr/share/unity-2d folder, hoping upon reinstalling Unity 2d (again) everything will come back to normal. But it didn't. Reinstalled unity 2d, logged in to Unity 2d session, but now the whole top panel is messed up, as well as the launcher, and the folder usr/share/unity-2d is not there (I was hoping it will be created upon re-installation). 
So now I'm stuck. I'd really like to give Unity a shot, even if it's the 2d version, but I don't know how to reverse all the crap I did and get it back in its original state.
Any suggestions?
Thx, 
Radu

---

### Post by wildmanne39 on 2011-05-16
> **rereradu said:**
> I updated to 11.04 but Unity was slowing down my computer significantly so I installed Unity 2D, which worked like a charm. Until I went around messing with it pretty bad. 
What I did:
I tried to change the launcher icons, so I went and edited  Launcher.qml, LauncherList.qml and LauncherItem.qml following some instructions I found [here]("http://bhou.wordpress.com/2011/05/06/change-the-icon-size-in-unity-2d-launcher/"). Reckless enough, I did not make a back-up of these files (stupid!). After restarting Unity 2d, the launcher showed completly blank. I tried removing and reinstalling Unity 2d (from Ubuntu Classic session) but when logging in to Unity 2d session again, the launcher was still showing blank. So then I made another mistake... I removed the usr/share/unity-2d folder, hoping upon reinstalling Unity 2d (again) everything will come back to normal. But it didn't. Reinstalled unity 2d, logged in to Unity 2d session, but now the whole top panel is messed up, as well as the launcher, and the folder usr/share/unity-2d is not there (I was hoping it will be created upon re-installation). 
So now I'm stuck. I'd really like to give Unity a shot, even if it's the 2d version, but I don't know how to reverse all the crap I did and get it back in its original state.
Any suggestions?
Thx, 
Radu
Hi, just open a terminal by hitting alt+f2 or ctrl +alt+t and type unity --reset  and let it run for about three minutes, do not worry about the errors it will list, then hit ctrl+alt+del to restart the computer and everything should be fine.:D

---

### Post by NormanFLinux on 2011-05-16
With 2D, you add programs with a right click.

For the few programs you can't, if you know how to create a desktop. file, you launch gconf-editor, go to desktop, unity, launcher, and then add it to the favorites key. You can also arrange the icons there as you like.

Logout and login again to confirm your changes, including adding a new program to the launcher.

---

### Post by rereradu on 2011-05-16
Thanks for the reply. I did try to run unity --reset while logged in to Unity 2d session, but that only activates Unity 3d, while Unity 2d is still messed up and both are interacting quite ugly. I need to find out a way to restore the original unity-2d folder with whatever it was containing and get Unity 2d in its original state. Any suggestions, anyone?

> **NormanFLinux said:**
> With 2D, you add programs with a right click.

For the few programs you can't, if you know how to create a desktop.  file, you launch gconf-editor, go to desktop, unity, launcher, and then  add it to the favorites key. You can also arrange the icons there as you  like.

Logout and login again to confirm your changes, including adding a new program to the launcher.

I know this. What I don't know is how to get Unity 2d to actually work again, like undoing the unity-2d folder remove and all (see my first post).

---

### Post by NormanFLinux on 2011-05-16
Uninstall 2D. And then try to do a fresh install. Short of that, you may have to reinstall Ubuntu and take note not to mess around with ANY folders. If you don't know what you're doing, leave well enough alone!

---

