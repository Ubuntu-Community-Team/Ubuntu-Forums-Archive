---
title: "Missing Unity Desktop, Though Apparently It's Enabled At Login; How Do I Fix This?"
date: 2011-05-16
forum: Desktop Environments
---

### Post by OzzyFrank on 2011-05-16
Hi. I just upgraded to 11.04, and while I originally Googled to see if I could keep my "classic" Gnome desktop, I actually wouldn't mind having a look at the new way of doing things.

Now, I am fully aware how to change from "Ubuntu" (meaning Unity) to the "Classic" modes at the login screen, as I already looked that up to help others who upgraded before me. In those cases, they were still set to log in to the Classic desktop, so had to manually change to the Unity option. However, mine was already set to "Ubuntu", but because of nVidia drivers I needed to reinstall, was told I didn't have the hardware to run Unity, so I should login again and choose Classic. It continued to what I thought was the old desktop, and after reinstalling the drivers and rebooting, I noticed it was actually set to "Ubuntu", not the Classic mode.

So how do I enable Unity when apparently I am in a desktop running it? Any info on this, and how to get Emerald themes happening again (when it is apparently already enabled as the window decorator), would be greatly appreciated. Cheers

---

### Post by Krytarik on 2011-05-16
Are you having the usual Gnome Panels in the session you are getting?
Are you still getting the mentioned error message?

Run this to check if your current video hardware/driver setup is able to run Unity, and what video driver is running:
```
/usr/lib/nux/unity_support_test -p
```For further info, please see this troubleshooting guide:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

The current Emerald package in the official repos of Natty doesn't work with the current version of Compiz.
But you could try to compile it yourself:
[http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/](http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/)

Greetings.

---

### Post by OzzyFrank on 2011-05-16
That command just returns **No such file or directory** because that path doesn't exist on my machine.

All my Gnome panels are as before (customised). I never received that message again, but then I immediately installed the required nVidia drivers.

Also, desktop effects work, BUT I have to use the Compiz Icon to reload the window manager to get it to work. Emerald isn't happening, but I can change the GTK+/Metacity border via Appearance.

---

### Post by OzzyFrank on 2011-05-16
$ **unity --reset**
[COLOR="Red"]The program 'unity' is currently not installed.  You can install it by typing:
sudo apt-get install unity[/COLOR]

Could this be a factor?? I assume it's not talking about some other "unity" command/program... but I figured the Unity interface was installed with 11.04 whether one wanted it or not. And since I got that message about my hardware and Unity, I would assume it is on my system. But I thought I better share that...

---

### Post by Krytarik on 2011-05-17
> **OzzyFrank said:**
> I assume it's not talking about some other "unity" command/program...
Indeed, it is!

To install it and to make sure every other packages listed as dependencies of "ubuntu-desktop" are/will be installed as well, run:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by wildmanne39 on 2011-05-17
> **OzzyFrank said:**
> $ **unity --reset**
[COLOR="Red"]The program 'unity' is currently not installed.  You can install it by typing:
sudo apt-get install unity[/COLOR]

Could this be a factor?? I assume it's not talking about some other "unity" command/program... but I figured the Unity interface was installed with 11.04 whether one wanted it or not. And since I got that message about my hardware and Unity, I would assume it is on my system. But I thought I better share that...
Hi, yes that is the problem, run that command.:)

---

### Post by wildmanne39 on 2011-05-17
> **OzzyFrank said:**
> $ **unity --reset**
[COLOR="Red"]The program 'unity' is currently not installed.  You can install it by typing:
sudo apt-get install unity[/COLOR]

Could this be a factor?? I assume it's not talking about some other "unity" command/program... but I figured the Unity interface was installed with 11.04 whether one wanted it or not. And since I got that message about my hardware and Unity, I would assume it is on my system. But I thought I better share that...

Hi, I just noticed that I was not clear the command is sudo apt-get install unity.:D

---

### Post by OzzyFrank on 2011-05-17
OK, I really should have just opened Synaptic and had a look myself, but with all the hoo-hah about Unity, it NOT being installed along with 11.04 kind of took me by surprise... especially since I got that message about Unity not being able to run (that sort of implies to me it is installed, but obviously I was wrong).

So yeah, once I saw it wasn't installed, I just marked it (and dependencies) for installation while I was there. And now I know why I couldn't find Ubuntu Unity Plugin in the Compiz settings manager. Once I enabled that, and resolved some plugin conflicts, it was up and running without needing to log out or reboot.

And I didn't install "ubuntu-desktop" since I always break the hell out of it (meaning some packages I've uninstalled, and others conflict with that metapackage).

For any who follow, just run **[COLOR="Red"]sudo apt-get install unity[/COLOR]** in a terminal and it will install all dependent packages automatically, then _enable the Unity plugin_ under "Desktop" in **CompizConfig Settings Manager** (**[COLOR="Red"]sudo apt-get install ccsm[/COLOR]** if you don't have it).

---

### Post by OzzyFrank on 2011-05-17
While I am here, and out of curiosity, how come some people seem to have **unity_support_test** on their systems, while others don't?

---

### Post by wildmanne39 on 2011-05-17
> **OzzyFrank said:**
> While I am here, and out of curiosity, how come some people seem to have **unity_support_test** on their systems, while others don't?

Hi, probably because people only use it after unity does not work,also if you want compiz you need to log out and hit your user name and go to the bottom of the screen and click ubuntu classic and you can enable effects, I am running the cube and full effects in classic mode no problem at all, if you try in regular unity you will break it because the do not play well together.:)

---

### Post by Krytarik on 2011-05-17
> **OzzyFrank said:**
> **CompizConfig Settings Manager** (**[COLOR=Red]sudo apt-get install ccsm[/COLOR]** if you don't have it).
Actually, the package is called "compizconfig-settings-manager" (common mistake though). ;)
> **OzzyFrank said:**
> While I am here, and out of curiosity, how come some people seem to have **unity_support_test** on their systems, while others don't?
Because you don't have the "ubuntu-desktop" metapackage installed and did an upgrade.

The mentioned tool is included by the package "nux-tools", which is a dependency of "unity", which is a dependency of "ubuntu-desktop".

So, that's why it's generally no such a good idea to kill the metapackages and leave them as such.

Also, the reason why you nevertheless got an error message upon login that made you believe that Unity is installed, is that the session settings are included by the packages "gnome-session" and "gnome-session-common", which were both installed at your system before.

The part of the Unity session settings that responsible to check if Unity is supported, is to run exactly "unity_support_test".
And because it wasn't even installed, that just errored out, and you got the same error message as if Unity isn't supported.
```
[GNOME Session]
Name=Ubuntu
Required=windowmanager;panel;filemanager;
Required-windowmanager=compiz
Required-panel=compiz
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;
**IsRunnableHelper=/usr/lib/nux/unity_support_test**
FallbackSessionsID=FallbackUnity2d;FallbackClassicGnome
FallbackUnity2d=2d-ubuntu
FallbackClassicGnome=classic-gnome
**FallbackClassicGnomeMessage=It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment.**
```> **wildmanne39 said:**
> if you want compiz you need to log out and hit your user name and go to the bottom of the screen and click ubuntu classic and you can enable effects, I am running the cube and full effects in classic mode no problem at all, if you try in regular unity you will break it because the do not play well together.:)
Please stop stating that! I noticed that you did that in a couple of other threads as well. You know what, Unity is a plugin of Compiz, and it's in fact more effect-heavy than the usual user ever saw before! And it's also possible to run the Cube alongside to it, with a bit effort:
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Greetings.

---

### Post by wildmanne39 on 2011-05-17
> **Krytarik said:**
> Actually, the package is called "compizconfig-settings-manager" (common mistake though). ;)

Because you don't have the "ubuntu-desktop" metapackage installed and did an upgrade.

The mentioned tool is included by the package "nux-tools", which is a dependency of "unity", which is a dependency of "ubuntu-desktop".

So, that's why it's generally no such a good idea to kill the metapackages and leave them as such.

Also, the reason why you nevertheless got an error message upon login that made you believe that Unity is installed, is that the session settings are included by the packages "gnome-session" and "gnome-session-common", which were both installed at your system before.

The part of the Unity session settings that responsible to check if Unity is supported, is to run exactly "unity_support_test".
And because it wasn't even installed, that just errored out, and you got the same error message as if Unity isn't supported.
```
[GNOME Session]
Name=Ubuntu
Required=windowmanager;panel;filemanager;
Required-windowmanager=compiz
Required-panel=compiz
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;
**IsRunnableHelper=/usr/lib/nux/unity_support_test**
FallbackSessionsID=FallbackUnity2d;FallbackClassicGnome
FallbackUnity2d=2d-ubuntu
FallbackClassicGnome=classic-gnome
**FallbackClassicGnomeMessage=It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment.**
```
Please stop stating that! I noticed that you did that in a couple of other threads as well. You know what, Unity is a plugin of Compiz, and it's in fact more effect-heavy than the usual user ever saw before! And it's also possible to run the Cube alongside to it, with a bit effort:
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Greetings.

Hi, I know it is but when you enable the cube when logged in the regular unity it breaks unity and you have to use unity --reset or compiz reset to fix it and for new people it was creating a lot of frustration for them.

---

### Post by Krytarik on 2011-05-17
> **wildmanne39 said:**
> Hi, I know it is but when you enable the cube when logged in the regular unity it breaks unity and you have to use unity --reset or compiz reset to fix it and for new people it was creating a lot of frustration for them.
Yeah, it's indeed likely that the usual user breaks Unity upon the first try to enable the Cube. But it doesn't help that your statement doesn't reflect the facts and/or that particular issue at all. Instead it makes the reader believe that one can't run Compiz at all in a Unity session, which is painfully wrong. That, in turn, is capable to put of users to use Ubuntu at all if they somewhere picked up that Ubuntu will drop the classic Gnome session with the next release and they don't have a fair understanding of the various session options.

---

