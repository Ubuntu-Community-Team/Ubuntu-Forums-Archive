---
title: "Disappearing GNOME menu edits"
date: 2005-01-14
forum: Desktop Environments
---

### Post by NeoChaosX on 2005-01-14
Help! I recently installed some programs from the Hoary sources (Firefox, Gaim and XMMS, that's it) onto my Warty install, and after I rebooted GNOME, I noticed that my previous edits to the GNOME menu had disappeared. I hadn't installed any critical Hoary packages, and I could still access applications:// and see my edits in Nautilus, but they don't show up in the menu. Anybody know how to fix this?

---

### Post by zeroK on 2005-01-14
[QUOTE=NeoChaosX]Help! I recently installed some programs from the Hoary sources (Firefox, Gaim and XMMS, that's it), and after I rebooted GNOME, I noticed that my previous edits to the GNOME menu had disappeared. I hadn't installed any critical Hoary packages, and I could still access applications:// and see my edits in Nautilus, but they don't show up in the menu. Anybody know how to fix this?[/QUOTE]
Sorry, a little bit off topic :-( :
 O_o applications:// works again in gnome 2.9.4?

---

### Post by NeoChaosX on 2005-01-14
No, I didn't install anything from Hoary other than Firefox, Gaim and XMMS. Gnome is still 2.8.1.

---

### Post by NeoChaosX on 2005-01-14
So...anybody have any suggestions or idea on how to fix? :?

---

### Post by valadil on 2005-01-14
I'm guessing that the debian menu system got installed and took over.  It's a bitch when that happens.  Menu is a program that keeps a list of applications you've installed via apt and update-menu generates menus out of these lists of apps for all your window managers.  It's actually pretty cool, except that the first time you discover it is right after it kills your custom menus.

I can't remember how it all works exactly.  ~/.menu contains a bunch of files, each of which corresponds to an app you want in your menu.  update-menus generates menus from said files.  /etc/menu should point you towards better documentation of this.  Generally you can find an example of a menu file for one app and copy/edit it to handle any other app.

---

### Post by NeoChaosX on 2005-01-14
Aw, forget it, I installed Warty over again. Not touching Hoary packages again until it's finalized, stable and guaranteed not to break my menu.  :-&

---

### Post by wallijonn on 2005-01-14
[QUOTE=NeoChaosX]I installed Warty over again. Not touching Hoary packages again until it's finalized, stable and guaranteed not to break my menu.[/QUOTE]

That's the best thing to do. Re-installing Warty is good exercise. So will burning your data on a regular basis. Every change I've made I have documented so that I can get back to a workable state. So far my list is about 400 lines long. 

Play around with Warty, blow it up, re-install. It's a great way to learn. So far I have rebuilt my system at least three times. I just wish I could find that Gentto thread where a flag can be set in Linux to speed it up, like pre-fetching.

---

### Post by Karlos on 2005-01-16
ok...i have done the same thing

and i only upgraded gaim

...but I like the sound of this menu program ..... I just cant make head nor tail of any of the documentation that comes with it...

it looks like it can add an extra 'debian' menu somehow

Does anyone know of a tutorial anywhere for menu (the program)

or does anyone know how to work the program with the ubuntu gnome enviroment??

many thanx..Karlos

---

### Post by LongTooth on 2005-01-16
[QUOTE=wallijonn]That's the best thing to do. Re-installing Warty is good exercise. So will burning your data on a regular basis. Every change I've made I have documented so that I can get back to a workable state. So far my list is about 400 lines long. 

Play around with Warty, blow it up, re-install. It's a great way to learn. So far I have rebuilt my system at least three times. I just wish I could find that Gentto thread where a flag can be set in Linux to speed it up, like pre-fetching.[/QUOTE]


This is really the only way to learn. And even after all of these years with Linux, I'm still learning new things. For example, I just saved some steps by steps on how to install Tarballs. Something I've always stayed away from. Luckily I don't have anything of great importance on my Linux box. So if I do screw up my system I reinstall if I can't fix it. 

Another thing I've learned over the years is not jumping too quickly on the latest and greatest. Most of the time (for me anyway) its not worth the effort. Not much differences between version 1.0 and 1.1. I'm still using the Firefox 0.9.3 that came with Warty. Reading these forums leads me to belive upgrading to Firefox 1.0 can cause one to gnash their teeth or rip rainment and even put hair. 

I tend to stick to the packages that came with a version. And apt-get update and upgrade is the only thing I do. I find I have less problems.

---

### Post by macewan on 2005-01-16
[QUOTE=NeoChaosX]Aw, forget it, I installed Warty over again. Not touching Hoary packages again until it's finalized, stable and guaranteed not to break my menu.  :-&[/QUOTE]


It's recommended pretty much everywhere to read that Hoary is not suggested unless you welcome possible breaks.

Just use Warty and do the standard update & upgrades to be safe.

---

