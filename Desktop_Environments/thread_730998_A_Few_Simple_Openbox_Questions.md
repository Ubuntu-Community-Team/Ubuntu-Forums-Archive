---
title: "A Few Simple Openbox Questions"
date: 2008-03-21
forum: Desktop Environments
---

### Post by solarwind on 2008-03-21
I recently installed openbox and I have a few questions:

1. Where's the "dock"? I see the configuration for it in obconf but I don't see the dock on my screen.
2. How do I make it so that it doesn't show the window content while dragging or resizing?
3. I have no menu.xml file.

---

### Post by canistra on 2008-03-21
1. I am asking the same question :)
2. Why do you need that, no realy ))
3. Use Menu Maker, the install obmenu, and your set

---

### Post by solarwind on 2008-03-21
> **canistra said:**
> 1. I am asking the same question :)
2. Why do you need that, no realy ))
3. Use Menu Maker, the install obmenu, and your set

2. Umm... because it's faster.
3. What's Menu Maker?

---

### Post by canistra on 2008-03-21
1. No it's not ))) 
2. [http://menumaker.sourceforge.net/](http://menumaker.sourceforge.net/)

---

### Post by solarwind on 2008-03-21
> **canistra said:**
> 1. No it's not ))) 
2. [http://menumaker.sourceforge.net/](http://menumaker.sourceforge.net/)

1. I'm quite sure it is and I like it better.
2. Thanks!

---

### Post by solarwind on 2008-03-21
Ok, menu maker fixed my menu problem. Thanks a lot!

Now where did that dock go? And I really want to be able to drag/resize without the window contents being shown.

---

### Post by RedSquirrel on 2008-03-21
> **solarwind said:**
> Ok, menu maker fixed my menu problem. Thanks a lot!

Now where did that dock go? And I really want to be able to drag/resize without the window contents being shown.

For the menu, I would have thought running 'sudo update-menus' would have generated the default Openbox menu.


The main Openbox site has really good documentation:

[What is this dock I hear so much about?]("http://icculus.org/openbox/index.php/Help:FAQ#What_is_this_dock_I_hear_so_much_about.3F")

Edit: if you were thinking of a panel, Openbox doesn't come with one. I use fbpanel, but there are several to choose from (see the Openbox website), or you can simply not use one at all. ;)


See "update window contents while resizing" in obconf, under the "Move & Resize" tab. It won't completely blank the window though (that is, leaving only the window frame). I don't think you can do that in Openbox (?).

---

### Post by solarwind on 2008-03-21
> **RedSquirrel said:**
> For the menu, I would have thought running 'sudo update-menus' would have generated the default Openbox menu.


The main Openbox site has really good documentation:

[What is this dock I hear so much about?]("http://icculus.org/openbox/index.php/Help:FAQ#What_is_this_dock_I_hear_so_much_about.3F")

Edit: if you were thinking of a panel, Openbox doesn't come with one. I use fbpanel, but there are several to choose from (see the Openbox website), or you can simply not use one at all. ;)


See "update window contents while resizing" in obconf, under the "Move & Resize" tab. It won't completely blank the window though (that is, leaving only the window frame). I don't think you can do that in Openbox (?).
Thanks. Right now, I think I'll stick with Fluxbox though. It has all the functionality I need and is fast. Also looks really nice.

---

### Post by RedSquirrel on 2008-03-21
> **solarwind said:**
> Thanks. Right now, I think I'll stick with Fluxbox though. It has all the functionality I need and is fast. Also looks really nice.
Good choice. Fluxbox is very nice. The Fluxbox tutorial link in my signature might be of some help. Have fun! :)

---

### Post by solarwind on 2008-03-21
> **RedSquirrel said:**
> Good choice. Fluxbox is very nice. The Fluxbox tutorial link in my signature might be of some help. Have fun! :)

I got the menu working. For noobs like me, [fme]("http://code.google.com/p/fluxbox-menu-editor/") works perfectly.

---

### Post by eriqjaffe on 2008-03-22
I really like using [marchfluxmenu]("http://ubuntuforums.org/showthread.php?p=3800721&highlight=marchfluxmenu#post3800721"), myself.  I love the fact that it auto-updates the menu...

---

### Post by urukrama on 2008-03-24
If you still need help with Openbox, my [guide ]("http://urukrama.wordpress.com/openbox-guide/")might help.

---

### Post by solarwind on 2008-03-24
> **urukrama said:**
> If you still need help with Openbox, my [guide ]("http://urukrama.wordpress.com/openbox-guide/")might help.

Very nice. Thanks a lot!

---

