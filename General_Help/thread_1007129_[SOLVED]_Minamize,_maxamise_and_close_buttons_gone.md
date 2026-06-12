---
title: "[SOLVED] Minamize, maxamise and close buttons gone?"
date: 2008-12-10
forum: General Help
---

### Post by rswoody2000 on 2008-12-10
Hi all

I installed Ubuntu the other day and got it working well and decided to install Beryl. As soon as i installed it the group of icons on the top right corner of each window to minimise or close has gone. I am then unable to move the window or close it the usual way. What has caused that?

 I can get it back by changing the window manager back to compiz, but then as i am sure you know beryl effects don't work any more. Do i need to change something in beryl settings manager to get them back?

---

### Post by eternalnewbee on 2008-12-10
beryl is now called compiz-fusion.
What distro are you using? If you're either using 8.04 or 8.10, then compiz-fusion is installed by default.
You can find it under: **Main Menu > System > Preferences > CompizConfig Settings Manager**.
If it's not there, you can install it via S**ynaptic Package Manager** (**Main Menu > System > Administration**).

---

### Post by Forlong on 2008-12-10
> **Forlong said:**
> **get rid of Beryl right now. Beryl is dead.**

It is a discontinued project for over a year now, there hasn't been a release since **March 2007**. There is no support whatsoever.

The Beryl project has been succeed by the Compiz Fusion project, which is an enhancement of the Compiz window manager.
Both Compiz and the main components of Compiz Fusion are installed by default in Ubuntu 8.04

The root of your problem is most probably that you are trying to use the window decorators from Ubuntu's repositories. Those can not communicate with Beryl anymore, as they have been rewritten to run with Compiz.

So... un-install Beryl and whatever you installed with it. If you added a repository to install Beryl, get rid of it as fast as you can, because there is no repository for Beryl that works on Hardy.

If you need any assistance with that, just let me know.
From here: [Unable to miniimize, expand, close windows]("http://ubuntuforums.org/showthread.php?t=994751")

---

### Post by rswoody2000 on 2008-12-10
> **eternalnewbee said:**
> beryl is now called compiz-fusion.
What distro are you using? If you're either using 8.04 or 8.10, then compiz-fusion is installed by default.
You can find it under: **Main Menu > System > Preferences > CompizConfig Settings Manager**.
If it's not there, you can install it via S**ynaptic Package Manager** (**Main Menu > System > Administration**).

Aaah i see, that makes sense. If i only knew that came with the later versions of Ubuntu. I do have version 8.10 and i have done what you suggested as the CompizConfig Settings Manager didnt appear in the menu. I can use the program now but i need to get used to the different settings. 

I am having trouble getting the cube to work propely but would there be any complication or conflicts with me having beryl and compiz-fusion? I dont however see the burning effect in the compiz-fusion settings manager.

---

### Post by eternalnewbee on 2008-12-10
> I am having trouble getting the cube to work propely but would there be any complication or conflicts with me having beryl and compiz-fusion? I dont however see the burning effect in the compiz-fusion settings manager.
Like forlong said: Get rid of Beryl.
You can find the Burning Effect under Animation Addons and Animations.

---

### Post by rswoody2000 on 2008-12-10
> **eternalnewbee said:**
> beryl is now called compiz-fusion.
What distro are you using? If you're either using 8.04 or 8.10, then compiz-fusion is installed by default.
You can find it under: **Main Menu > System > Preferences > CompizConfig Settings Manager**.
If it's not there, you can install it via S**ynaptic Package Manager** (**Main Menu > System > Administration**).

Right i have done a lot of playing around and i think i got it sussed. I now preffer the Compiz-Fusion as i understand how a lot of it works now. I got the cube to work perfectly now and got my burn effect back after finding the addons. I like the fire writing effect. Cheers for your help, much appreciated.

---

### Post by eternalnewbee on 2008-12-10
You're welcome.
Glad your problems are history.
Btw, if you feel your issues are solved, please mark the thread as solved, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.

---

