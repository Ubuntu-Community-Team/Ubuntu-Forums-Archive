---
title: "panel - docky - mess"
date: 2010-05-30
forum: Desktop Environments
---

### Post by jbocean on 2010-05-30
Noob Here - 

Today I installed 10.04(!) I installed my codecs, Ubuntu Tweak, Mint Menu (Thanks Sn3ipen from another thread) and everything was going great until I attempted to install Docky - Current Issues:

1. When I installed Docky, I got a message saying something like "Enable Compositing Effects for Docky to run properly".

2. Well, I had already deleted my bottom panel and when Docky didn't work out, (bc it left like a quarter of the bottom of my screen black-where Docky was running), 
So I kept trying  to "Add Panel" to get the bottom panel back, which had no apparent effect - Until I uninstalled Docky and now ...

(a) I have a bottom panel which doesn't work (nothing shows up there) and
(b) I have like 35 little boxes of "ghost panels" on the right side of my screen - I have been assuming them to be from when I attempted to restore my bottom panel. 

3. If I "right click" in either the non-working  bottom panel or the right-sided "ghost panels", I get the choices "Help" or "About Panels".

So How Can I ...

4. Clean up the right side of my screen from all of those little squares.
5. Get a working bottom panel again.
6. What does enable compositing effects mean if I get brave and ambitious again and want to install Elementary theme or docky (again).

*  Never mind the hassles ... I am Thoroughly Impressed w/ 10.04!  
It is so cool and So-Much-Faster than my old Win-XP !!!

Thanks for any help

---

### Post by SnickerSnack on 2010-05-30
Have you tried restarting anything?  First, try "killall gnome-panel" from a terminal.  If that doesn't work, try logging out and starting a new session.  If that doesn't help, try rebooting.

"Enable compositing" means you need a compositing window manager, which metacity (the default window manager in gnome) is not.  You need to install compiz or use a different desktop environment.  Xfce would work.  I don't know if kde will.

---

### Post by jbocean on 2010-05-30
Wow - Thanks for quick reply.

* I have rebooted and therefore began a new session.
* If I "killall gnome-panel" ... will that wipe out the top panel and will I be able to get anything back?
    'killall' seems kinda ominous.

---

### Post by washburnello on 2010-05-30
Docky is a fantastic dock and I highly recommend using it. But is does require compiz to be running. If your working with a relatively fresh install of ubuntu and you don't have compiz running by default then one of two things is happening that i can think if.

1. Your computer's hardware is not powerful enough to run compiz or...
2. You need to enable some hardware drivers for your graphics card.

If the problem is 1. then docky is not an option and you will need to rebuild your bottom panel. (which isn't hard) just right click on the panel and select "add to panel" and put back your "Window List", Workspace Switcher", and "Trash" ect...
If the problem is 2. go to System > Administration > Hardware Drivers and see if it prompts you to install some drivers.

I would recommend trying to get compiz working first because it just makes Ubuntu so much nicer :)

Also it might be handy to post a screenshot to help clarify exactly what you mean by ghost panel. Just press the "Print Screen" button on your keyboard and upload the file with your reply.

If you really get to your witts end and have a gtalk account setup in empathy, I'd be more than happy to look at your desktop remotely. (Look, not touch ;) )

-John

---

### Post by nichipet on 2010-05-31
This page has a script that will reset gnome panels to their default:

[http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

I've used it, it worked for me.

---

### Post by stinkeye on 2010-05-31
> Docky is a fantastic dock and I highly recommend using it. But is does require compiz to be running.

Docky does not need compiz to run.
Metacity, the default window manager will run docky if you enable it's
compositing feature.

System tools > configuration editor
(If you can't find it, run **gconf-editor** in the terminal.

In gconf-editor go to /apps/metacity/general/compositing_manager
and tick the box.
While you've got gconf-editor open go to bookmarks and add bookmark,
so you can easily change it back if needed.

---

### Post by elidoperezmd on 2010-05-31
how shloud i address this problem? please see the attached image.

The icons are partialy hidden behind the panel, if i click an icon the docky will come on top of the panel for 5 to 10 mins, but will then got back partially hidden, how can i make is be on top always that i run my mouse on top of it.

Current setting for docky are autohide.

thanks for the time

---

### Post by Zemblan on 2010-05-31
I don't think it's a good idea to have gnome-panel and docky running on the same screen edge. The easiest solution is to move one of them to the bottom.

EDIT: ah just noticed you already have the default two panels, one top and one bottom. I use docky, but I use it replace the bottom panel, which I delete. I don't see the need to have a dock and the window list at the same time. If you want to you could have the window list in the top panel where there is empty space.

---

### Post by elidoperezmd on 2010-05-31
as opposed to this....this is want i want all the time

---

### Post by elidoperezmd on 2010-05-31
it does the same thing if i have docky running on the bottom of the screen.

Thanks for the reply

---

### Post by Zemblan on 2010-05-31
I understand what you want to do. Normally the dock would replace one of the panels. But if you want to have it in addition and always on top you will find instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=1274398](http://ubuntuforums.org/showthread.php?t=1274398)

---

### Post by elidoperezmd on 2010-05-31
> **Zemblan said:**
> I understand what you want to do. Normally the dock would replace one of the panels. But if you want to have it in addition and always on top you will find instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=1274398](http://ubuntuforums.org/showthread.php?t=1274398)

YOU DA MAN...Thanks...ill check it out right away

---

### Post by jbocean on 2010-05-31
nichipet Thanks !

I followed your link/directions and have restored the default panel settings !

I have an older Dell Dimension 4550 w/ 2gig memory which is dual-booting Win-XP and Ubuntu Lucid. I did check proprietary drivers and found the suggested Nvidia driver is already running. I checked Compiz and that seems to be up and running as well. 

Perhaps since this is an older machine which is doing double(boot)-duty,
I may be better off to consider leaving well-enough alone and not trying to run Docky.

Thanks to everyone here who have helped to make my introduction into Ubuntu a positive one. For me anyway, this has been solved.

---

