---
title: "Applications menu on the gnome panel is now empty :("
date: 2008-06-03
forum: Desktop Environments
---

### Post by djrobthaman on 2008-06-03
Hi everyone,

My gnome panel menu is giving me some major problems.  The "Applications" menu is no longer displaying any items.  Att the same time, though, places and system are both populated with the usual items.

I've looked in my usr/share/applications folder and it is not empty.  I notice a lot of the things that used to be in the applications menu (I guess that's why a lot of people online say "that's where you're applications menu items are stored").

I've tried restarting.

I've tried killall gnome-panel (it obviously gets killed but quickly regenerates itself like the spawn of satan that it is).

I've tried removing the applet and re-adding it to the panel.

I've tried right-clicking it and selecting "edit menus" (nothing happens... the window never opens).

The last thing I remember doing before first noticing there was a problem was replacing the config folder in my home folder for avant windows navigator.  That shouldn't affect it

Anybody know anything I can try to get this thing populated again?

Thanks

---

### Post by pytheas22 on 2008-06-03
If you don't mind losing your Gnome settings, renaming the .gnome2 directory with the command:
```

mv ~/.gnome2 ~/.gnome2-old
```

would most likely solve the problem.  Maybe someone else could tell you more specifically where to look to fix the issue, however.

---

### Post by prostar on 2008-06-03
I've also had this since updating my AMD64 7.10(Gutsy) install to Kernel 2.6.22-14.  Some of the obvious suggestions improved my usability but I am still having problems.  The virtual consoles don't work(Alt+F1-4), can't shutdown/restart, lost my window theme, and of course the panels (were) useless.

While I have fixed the panels by removing apps and configs until they worked again, there is still something drastically wrong.  I noticed the system load was near 5.00 (but no CPU usage).  I have "gnome-settings-deamon" and "mixer_applet2" running "Uninterruptable" and can't kill them (not even as root "kill -9" or "killall -HUP".  If I go to set a new theme I get an error that gnome-settings deamon can't be started.  I always dread kernel updates, but always can't resist either....

BTW: Using the previous kernel (2.6.20 something) will not boot at all now.

---

### Post by VMC on 2008-06-03
You might want to try the GUI,  System > Preferences > Main menu, and Applications menu options should come up. Look at the right under Items and see if anything checked.

You can always to the above solution to rebuild your menus.

---

### Post by djrobthaman on 2008-06-04
> **pytheas22 said:**
> If you don't mind losing your Gnome settings, renaming the .gnome2 directory with the command:
```

mv ~/.gnome2 ~/.gnome2-old
```

would most likely solve the problem.  Maybe someone else could tell you more specifically where to look to fix the issue, however.

> **VMC said:**
> You might want to try the GUI,  System > Preferences > Main menu, and Applications menu options should come up. Look at the right under Items and see if anything checked.

You can always to the above solution to rebuild your menus.

Thanks for the suggestions, but neither of these worked.  The main menu program didn't ever open and a new folder was created automatically for the gnome config, but there are still no items in my applications menu :(

Is there anything else I can do?

---

### Post by pytheas22 on 2008-06-04
Try creating a new user account (go to System>Administration>Users and Groups) and log in under it.  Does the menu work under the new account?  This will tell us whether the problem lies with Gnome itself or some local user setting.

---

### Post by prostar on 2008-06-04
To the OP, if you can get a terminal in Gnome (Alt-F2), then just run "alacarte" to edit your menus.  If it doesn't run use "gksudo synaptic" and install/reinstall alacarte.

In my case, the menus aren't really the problem, I have them working again.  It's Gnome in general that went ape S**T since the kernel upgrade.  I don't want to hit the shiny red dist-upgrade to Hardy for fear of 64-bit issues that I was just getting worked out from the upgrade to gutsy.

---

### Post by OmniCloud on 2008-06-04
> **prostar said:**
> To the OP, if you can get a terminal in Gnome (Alt-F2), then just run "alacarte" to edit your menus.  If it doesn't run use "gksudo synaptic" and install/reinstall alacarte.

In my case, the menus aren't really the problem, I have them working again.  It's Gnome in general that went ape S**T since the kernel upgrade.  I don't want to hit the shiny red dist-upgrade to Hardy for fear of 64-bit issues that I was just getting worked out from the upgrade to gutsy.I recommend trying live CD's of different distros and newer version of Distro's. It's a good way to test out how it will run on your hardware. I was skeptical about Hardy as well, but did a live cd test, it detected all my hardware fine, and tbh, I haven't had any of the problems popping up in all these threads:confused:

Newer releases also have some pretty cool hardware detection GUI that will easily let you know everything that was detected automatically. A good indicator of how your hardware will mesh with the OS.

---

### Post by djrobthaman on 2008-06-05
> **pytheas22 said:**
> Try creating a new user account (go to System>Administration>Users and Groups) and log in under it.  Does the menu work under the new account?  This will tell us whether the problem lies with Gnome itself or some local user setting.

Pytheas, this worked, in the sense that my test user had applications in the menu.  But when I copied over config files I got a major error every time I logged in as myself again (I would log in and then get booted off and it would give me an error about being logged in for less than 10 seconds).  I fixed that by logging into the test account then using su in terminal and deleting those folders I moved.  Then I could log in but still with no applications.

What I ended up doing was reinstalling.  I wanted to install the 64 bit version of gutsy anyway (was using 32 bit... had a bad run in with the 64 bit edgy and have been hesitant to install that version ever since).

Thanks for your help though.  It was obviously the first step in the right direction.

---

### Post by pytheas22 on 2008-06-05
Sorry you didn't find a real solution, but at least you know now where the problem lay.  If you're worried about this happening again, it might not be a bad idea to periodically back up working configurations of your home directory, or at least of the hidden folders in it (i.e. the ones containing configuration information).  But hopefully the problem won't occur again.

---

### Post by djrobthaman on 2008-06-05
Yeah, I'm keeping my fingers crossed on that one.

---

### Post by Wolki on 2008-06-05
It seems I'm too late... I've had the same thing happening once, and the problem was a broken file in ~/.local/share/applications, and removing it made it work again.

---

### Post by djrobthaman on 2008-06-06
ooo... well I guess next time I'll know.

Thanks :)

---

### Post by jcanfield on 2008-08-08
[Solved] Okay, so I had the same problem. I upgraded to Hardy about three days ago. All seems well, except that I turned on my laptop and logged into gnome. I went to 'Applications' and the menu was empty. I had to idea what happened? 

So load up a terminal and '/usr/bin/gmenu-simple-editor'. Then click defaults and your Applications menu is right back where it was. (One of my folders was combined with 'Other', not a big problem though).

All in all I have no clue why that happened but it did and was an annoyance.

---

### Post by gmalac on 2008-08-09
Jcanfield, you just saved my life!
Thanks!

---

### Post by Brandel Valico on 2008-08-09
There are also a few other threads about this.

[http://ubuntuforums.org/showthread.php?t=554585&page=3](http://ubuntuforums.org/showthread.php?t=554585&page=3)

[http://ubuntuforums.org/showthread.php?t=166238](http://ubuntuforums.org/showthread.php?t=166238)

[http://ubuntuforums.org/showthread.php?t=541964](http://ubuntuforums.org/showthread.php?t=541964)

---

### Post by guitarrarl on 2009-12-20
Hi friends: I am having the same problem but created a new user and the Applications menue did work. I will tray all the following tips or methods and see what I get :)
Thanks!
RL
hppt://www.afn.org/~guitarra/

> **Wolki said:**
> It seems I'm too late... I've had the same thing happening once, and the problem was a broken file in ~/.local/share/applications, and removing it made it work again.

---

### Post by guitarrarl on 2009-12-20
Hi Jcanfield:  Yes this works, Thanks! :P

RL
> **jcanfield said:**
> [Solved] Okay, so I had the same problem. I upgraded to Hardy about three days ago. All seems well, except that I turned on my laptop and logged into gnome. I went to 'Applications' and the menu was empty. I had to idea what happened? 

So load up a terminal and '/usr/bin/gmenu-simple-editor'. Then click defaults and your Applications menu is right back where it was. (One of my folders was combined with 'Other', not a big problem though).

All in all I have no clue why that happened but it did and was an annoyance.

---

