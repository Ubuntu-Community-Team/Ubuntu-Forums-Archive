---
title: "Gnome Shell + Unity Menu Style?"
date: 2012-09-09
forum: Desktop Environments
---

### Post by jim_deadlock on 2012-09-09
I've been using Unity since it was released but I've recently switched to Gnome Shell. I really like it but I miss the Unity-style menus that appear on the top panel rather than each individual window. Now I'm expecting a resounding "no" to this question but I thought I'd ask it anyway: is there a way to have Gnome Shell with the Unity-style panel menus?

---

### Post by markbl on 2012-09-09
jim, what you are asking about is called "global menus" which is what Unity uses. There is a huge history and enormous discussion about this. There used to be a ppa which gave global menus in gnome-shell but it seems not to be supported anymore. I think that is because gnome-shell has more recently gone off and implemented their own concept for "application menus". See [https://live.gnome.org/GnomeShell/Design/Whiteboards/AppMenu](https://live.gnome.org/GnomeShell/Design/Whiteboards/AppMenu). It is a slightly different concept to global menus and not really compatible.

---

### Post by jim_deadlock on 2012-09-09
That looks wonderful, is it available now or just a proposal? It's not very clear from the info page.

---

### Post by markbl on 2012-09-09
> **jim_deadlock said:**
> That looks wonderful, is it available now or just a proposal? It's not very clear from the info page.
If you use gnome-shell 3.4 on current ubuntu 12.04 you will already see the global application menu on most gtk apps. However most apps currently only offer a "Quit" menu option. Gnome expects that gnome apps going forward will start implementing more options in their application menu.

---

### Post by jim_deadlock on 2012-09-09
Yes I have 12.04/3.4 and I see the Quit option. So you're saying each individual app would have to be updated to work with the Appmenu? Won't that take forever and look like a total mess with some apps using the appmenu and others not in the meantime?

EDIT: am I right in thinking that when the options show on the Appmenu, they disappear from the individual window?

---

### Post by markbl on 2012-09-09
> **jim_deadlock said:**
> 
EDIT: am I right in thinking that when the options show on the Appmenu, they disappear from the individual window?
Gnome want apps to migrate to their new philosophy. That is instead of mixing global and window specific options in the menus of **all** open windows of an application, gtk apps would start migrating to the idea that they put their app global options (like preferences, app quit, etc) in the application menu (i.e. the "global" menu that appears in the top panel), and only window specific options in window menus. Many apps will choose not to have any menus on windows, e.g. just offer right click window options. Thus Gnome are encouraging app authors to migrate thoughtfully to global menus unlike Unity which has just software intercepted the focused window menu and put it in the main panel. The gnome idea makes sense really but yes it will take time for gtk app authors to implement this. ATM, gnome are "duplicating" the quit option in the application menu because it is universal and they want to show at least one option there.

---

### Post by jim_deadlock on 2012-09-09
Thanks for the info, very interesting. The Gnome 'democratic' method seems like it's going to be long and painful, like pulling teeth. Coming from Unity I find the window menus irritating, it's wasted screen space. I suppose I'll get used to it like anything else though.

---

### Post by xenon2185 on 2013-04-28
I couldn't agree with you more [COLOR=#000000]im_deadlock. Unity like global menu is the only feature I miss in Gnome 3. It's such a waste of screen space. 
Any recent news on the subject? Any hack to use global menu (not dropdown, but the one from Unity) in Gnome?[/COLOR]

---

### Post by jim_deadlock on 2013-04-28
Nautilus in 13.04 now has a lovely global menu, it's a start I suppose. I don't know of any hack.

---

### Post by Frogs Hair on 2013-04-28
I don't if this project died in 2011 or not . [http://www.webupd8.org/2011/11/install-gnome-shell-global-menu-in.html](http://www.webupd8.org/2011/11/install-gnome-shell-global-menu-in.html)

---

### Post by jim_deadlock on 2013-04-28
Yes it did sadly.

---

### Post by Cardale on 2013-06-10
Anyone willing to pick this project back up?

---

