---
title: "Feisty Fawn: Beryl and Out-of-box Gnome Effects Manager Conflict"
date: 2007-08-26
forum: Desktop Effects &amp; Customization
---

### Post by Denizen08 on 2007-08-26
While I am a new Linux user I have successfully installed ubuntu (7.04) Feisty Fawn on my Laptop. So far everything out-of-box (or native in-cd) works well. I am using the normal ubuntu with its native Gnome. And recently I have downloaded several programs from the repository(ies), one of them is beryl.

My Problem:
As I have found out Gnome has adopted some of the desktop effects of beryl thus making it similar in appearance to beryl, but I found this lacking so I downloaded beryl. After I've installed it, it seems to confict with Gnome during startup, hence I get a slightly slowed startup and an error message saying that some of Gnome's components (related to what functions beryl override) have failed to initiate.

As a result my startup uses the native Gnome, then I have to manually start Beryl for it to take effect (\take over).

What can I do to make beryl the primary during startup, without having to remove that of Gnome's (it can be used as a fall back in case Beryl crashes or fails)?

---

### Post by yuri_rage on 2007-08-26
I recommend simply uninstalling the included Desktop Effects package and Beryl and installing Compiz Fusion (the latest and greatest from opencompositing.org).  I followed the instructions on this site, and it worked very well (with the exception of using Envy to install nVidia drivers - use the Restricted Drivers tool included with Feisty instead):

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

Once Compiz is installed and working, you can add the "compiz --replace" command to your startup programs in the Sessions tool located in the System menu.

---

### Post by Denizen08 on 2007-08-26
Ok, I did what you said. I followed the web instructions and have successfuly installed Compiz, but one effect doesn't seem to work: the Desktop Cube. Even though its enabled in the manager it wont work, and everytime I change workspace it just fades in. Compiz has not totally taken over Metacity's functions...

Also I have added the command 'compiz --replace' in session startup. Other effects inherent to Compiz works, just not all of it... ><

---

### Post by yuri_rage on 2007-08-26
Do you have both the Desktop Cube and Rotate Cube plugins active?

---

### Post by Denizen08 on 2007-08-28
Actually I didn´t have any set to active, heck I even uninstalled all Desktop enhancement configs and management programs and left Metacity (the default) but all the effects remained... 

Nevermind my initial post. I reinstalled Linux instead, because I tinkered with it a bit and it seemed buggy from so much messing around. Anyway, I have a fresh desktop and I want to install Compiz or Compiz-fusion: Which is best, based on your experience and how do I install the latest? The compiz in the official repository is some version older than the latest; Where can I find/get the latest but stable release of Compiz for Feisty?

Btw, if I follow your initial post instead do I keep the default Metacity as a fallback desktop manager, and is there a better way than ´--replace´. I tried Emerald before but it wont start-up at start-up.

Thanks a lot for corresponding, and I´m sorry for being too persistent with my questions... I´m kinda trying my feel with Linux. ^^

Edit: I used forlong's howto instead and so far no bugs. As far as my problem is concerned, its solved now. :D

---

### Post by yuri_rage on 2007-08-28
I recommend following the instructions on the website I posted earlier.  It's the latest stable release of fusion.

I tried starting compiz from gdm, but it used default settings instead of my personal user account settings.  Now I just run compiz --replace as a "startup" program.  It's not elegant, but it works just fine.

---

