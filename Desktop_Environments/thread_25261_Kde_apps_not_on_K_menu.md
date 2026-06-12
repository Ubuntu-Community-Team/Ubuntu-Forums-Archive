---
title: "Kde apps not on K menu"
date: 2005-04-09
forum: Desktop Environments
---

### Post by abovett on 2005-04-09
Hi

I've installed kubuntu onto a couple of existing ubuntu (hoary) systems. Works, except  on one of the systems most of the KDE apps aren't present in the KDE menu (even though they've been added to the Gnome menus). The apps that were installed with Ubuntu are there but not the ones that got added with Kubuntu.

Can someone help? Perhaps point me to info on how the menus in ubuntu (gnome) and kubuntu (kde) are constructed? I know that the .desktop files are involved (at least with gnome), and I've hade a look at freedesktop.org, but I'm still not clear on exactly how the menus are constructed and why my KDE menus have apps missing.

Thanks

Andy B

---

### Post by humanity_to_others on 2005-04-09
Kde already has a menu tool so you can update menu.

---

### Post by digby on 2005-04-09
And you can find this menu editor by right clicking on the K menu icon and selecting the aforementioned editor.  Now the challenge is finding where everything is hidden in the filesystem... looking for anything in particular?

---

### Post by abovett on 2005-04-10
Thanks both for your answers, but the problem I'm trying to solve is rather more complex than that. I know about the menu editor but that's another problem - it won't run from my main account.

Since my last post I've read up some more on the way freedesktop.org compliant menus are meant to work, especially in KDE, so I understand a bit about how the .desktop, .menu and .directory files work, but further tests on the problem system have deepened the mystery even further (for me, anyway).

I decided to try to determine if it was a system or user-specific problem, so this is what I did:

1. I created a new user and logged in using KDE. Everything looked good - the menus were fully populated. So - I thought - this implies it's a user specific thing - something in my home directory is screwed?

2. To test the above theory, I temporarily removed my home directory (sounds drastic but it's not really - logged in as a different user, sudo -s to root, rename my home directory, create a new empty one with same ownership and group). Then I logged in as the normal user using KDE. Got the normal new user wizard and a default desktop - and no KDE apps in the menu still!

So - it's _not_ something in my home directory, but it _is_ associated with my normal user account. Any ideas, anyone?

--- UPDATE - Solved it!

Sometimes writing things down gets your thoughts into gear. Soon after I posted the above message the penny dropped. The clue was in the last line I wrote...

The problem was the kde cache in /var/tmp - there's one for each user and mine had become messed up. Delete it and all the apps reappeared and the menu editor started working.

It's easy to get used to thinking that all a user's files are in their home directory, but of course it's not quite true - /var and /tmp in particular can hold user specific files as well.

Cheers

Andy B

---

### Post by manny on 2005-04-21
Wow, thanks abovett! I was unable to edit my menu and had no clue at all, nice finding!

---

### Post by zolookas on 2005-04-22
Press K button->Run command... Enter:
```
kappfinder
```  then press enter again.
Press scan button. Press apply and close the program.

---

### Post by quini on 2005-06-25
[QUOTE=abovett]The problem was the kde cache in /var/tmp - there's one for each user and mine had become messed up. Delete it and all the apps reappeared and the menu editor started working.[/QUOTE]

Unfortunately that doesn't work for me.  I've installed pingus; after that, there was no "jocs" entry in K menu (games in catalan language), and your solution didn't work for me, don't know why...

I logged out, switched to console, removed all /tmp/ and /var/tmp/ user related directories/files and rebooted.

Any other idea?   ](*,)

---

