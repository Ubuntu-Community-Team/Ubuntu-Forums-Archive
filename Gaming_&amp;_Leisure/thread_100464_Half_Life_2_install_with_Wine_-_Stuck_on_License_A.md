---
title: "Half Life 2 install with Wine - Stuck on License Agreement"
date: 2005-12-07
forum: Gaming &amp; Leisure
---

### Post by zi99y on 2005-12-07
Hello,

I've been beavering away trying to install Wine in order to get Half Life 2 installed - which I've heard is possible. I've read through this guide here:

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17)

But unfortunately as soon as the Steam install gets to the license agreement, it does not allow you to proceed as the agree/disagree buttons don't respond to keyboard or mouse input.

I have even tried rebuilding wine from the source to ensure it's correctly configured for my system, using the info at the bottom of this page:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Anyone else heard of this problem, or know of a way I can get HL2 installed, I'd be much obliged.

---

### Post by byoon on 2005-12-07
I got HL2 installed using wine 0.9.1 from the debian repositories found on winhq.

HL2 and CSS don't run at an acceptable level.  I only get about 1 FPS having an AMD XP 2000+, 1 GB RAM, 128 MB 6600GT, Ubuntu Breezy.

If you can do better, I would love to hear about it.

As for button and input focus problems during install and account log in, try right mouse clicking the input box and selecting paste or try right mouse clicking  somewhere in the license agreement text and selecting paste and then hitting tab.

For some reason, this would allow the window to grab focus.

---

### Post by zi99y on 2005-12-07
Tried all of that, I've been clicking like a madman for ages trying to find a way in!! It's not at the login point though, the very early stage of the steam install, like 2 screens in. It won't allow the right click or paste anywhere, but I can select text in the license agreement. It looks like a wine incompatibility... Did you use any magic switches when you ran the install? I just use 
```
wine setup.exe
```

---

### Post by byoon on 2005-12-07
I used the SteamInstall.exe program found on [www.steampowered.com](www.steampowered.com).

I then allowed Steam to download the data for whichever game I wanted to run.

---

### Post by YokoZar on 2005-12-08
Try opening up winecfg from a terminal, and then adding a new application for steam.  Set it to run in a window, then set it to log in automatically after it lets you type in your password, then set it to run normally.

This is in the howto from Steam's entry in the AppDB, I think.

---

### Post by gil-galad on 2005-12-08
[QUOTE=YokoZar]
This is in the howto from Steam's entry in the AppDB, I think.[/QUOTE]

Yep, look at the steam entry in AppDB to get it working.

---

### Post by Supertip on 2006-05-10
To make sure you actualy read the agreement, Valve wants you to scroll down before you get the option to accept/decline, so scroll all the way down and the become available, but now i am stuck at the "Select Which Fetures You Want To Install", i selected HL2 but when i press next it says you must install in an existing steam folder, which i am already in, any ideas? do u have the same problem?

---

