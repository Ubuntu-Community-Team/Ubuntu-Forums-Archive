---
title: "Unity desktop does not interact and does not show the content of Desktop folder"
date: 2013-05-27
forum: Desktop Environments
---

### Post by Messzir on 2013-05-27
Hello folks,

The day before yesterday I tried to tweak my Unity's appearence with, you know, kinda 3D cube desktop, wobbling windows and so on, but unfortunately it has crashed. Luckily, before that I installed the gnome-fallback so I could use my computer via graphical interface, because when I tried to log in with Unity (listed as Ubuntu) it simply did not load the launcher and only the background was shown.

I reinstalled Unity several times, but it did not helped. After that, I tought angrily I shall reinstall the whole ubuntu because of it's dump interface, but then for a try, I logged in as another untouched and new user and it worked! Today, I deleted all the configuration files from my original account and it loads the launcher, but I experienced a really strange thing. Unity looks like it does not "enable" the Desktop in both accounts. It simply does not interact with clicks and does not show the content of my Desktop folder. I tried almost everything, spent hours with googling, but I could not find the solution. Have you got any ideas? It has become really annoying.

Thanks in advance!

---

### Post by Frogs Hair on 2013-05-27
Install the Tweak Tool and enable "Have File Manage Handle the Desktop". This enables the context menu and the ability to drag files onto the desktop.

---

### Post by Messzir on 2013-05-27
Thank you Sir, you have just saved my Ubuntu's life. :)

---

### Post by grahammechanical on 2013-05-27
For your information, Unity runs on top of a compositor/window manager called Compiz. That is what crashed. You do not say what version of Ubuntu you are using but the lastest two versions give us a warning of the ease with which we can break the desktop using Compiz Configuration Settings Manager (CCSM). Sometimes, if we can get to a working desktop we can use CCSM to set stuff to their default values or revert the changes we have made. I have found that it is best to make changes one at a time. Some changes to Compiz settings conflict with other Compiz settings.

---

### Post by Frogs Hair on 2013-05-27
> **Messzir said:**
> Thank you Sir, you have just saved my Ubuntu's life. :)

Your'e Welcome !

---

