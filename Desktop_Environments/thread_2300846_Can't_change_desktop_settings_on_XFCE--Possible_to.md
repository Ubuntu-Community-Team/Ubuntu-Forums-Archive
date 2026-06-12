---
title: "Can't change desktop settings on XFCE--Possible to have 2 environment managers at the"
date: 2015-10-28
forum: Desktop Environments
---

### Post by eyeonyouproductions on 2015-10-28
Hi all,

Slowly learning the Ins and Outs of Ubuntu here, runing 14.04 with XFCE desktop. I'm running into a problem with my desktop. It's not loading up the one I set up, and the Desktop Manager isn't changing anything. I can't set a Trash Icon on the desktop, for example. Also, I can't change the wallpaper, and when I go into the Desktop Manager, all those are set the same.

My theory is that I am using the wrong settings manager. Is that possible? I believe that the original desktop environment with Ubuntu is Unity, is that correct? Is it possible that I am changing Unity settings(Although the rest of the settings work) instead of XFCE settings, or that for some reason the Unity desktop is showing, while the rest of the session is correctly logged in to XFCE?

Lastly, how do I remove the extra desktop environments if there are any? AFAIK, I only have the default and XFCE, but maybe I played around with another for a few minutes before throwing it away. I did so much tweaking for the first 3 weeks that this is entirely possible. Lastly, is there any issue if I uninstall Unity completely? I'm assuming that there isn't, as this is the kind of functionality that is kinda of Linux' "thing", the ability to customize to pretty much any level.

Thanks in advance for any help., and I truly hope I haven't just made things confusing.

---

### Post by Frogs Hair on 2015-10-28
XFCE has it's own desktop settings and file manager and it is best to use the Thunar file manager that comes with XFCE. One of the problems with multiple desktops is clutter because all the applications for both desktops appear in the menu . The unity Appearance settings are available on the menu in XFCE but will not apply any changes in XFCE.

 When I last used XFCE the desktop icons were on the desktop by default and had to be removed manually. Are you seeing the Unity panel/ dash in XFCE ?

 Just a thought, if you don't have a lot of time and effort in the installation you might just want to backup and install Xubuntu instead of removing unity and all of its dependencies.

---

### Post by eyeonyouproductions on 2015-10-28
LOL, I DO have a ton of time in this one. I found the issue>>Nautilus was auto-launching and stealing control of the desktop. Now I have that cleared, just have to figure out why the desktop isn't launching, I just have to manually launch xfdesktop, so that's my next fix.

Thanks for the help!

---

