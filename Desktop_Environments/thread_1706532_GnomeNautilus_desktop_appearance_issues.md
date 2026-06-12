---
title: "Gnome/Nautilus desktop appearance issues"
date: 2011-03-14
forum: Desktop Environments
---

### Post by gofurygo on 2011-03-14
Hello

For quite a while now I have some issues with the menu panel and the window appearance. Better said, with its frequent "automated" change :(

Overall, there are 2 issues I would like to address in this post:
1) No icons being displayed in <System> menu from main panel
2) Randomly switching to Gnome-Icon-Set and/or theme on startup

1) The System drop-down menu doesnt show any icons at all and I wonder why. I went to edit the menu to check those entries but there, the icons are shown and assigned to the first 2 entries of the <System> menu. For some reason they wont show in the main panel menu --> see screenshot System_menu.png

2) Recently, when starting up Ubuntu, the desktop theme changes by itself, sometimes. Im getting some Gnome-Style desktop theme although I shut down the computer with Ambiance last time. As soon as I go to <Appearance>, _without_ re-selecting the Ambiance theme (just open the appearance dialog), it jumps back to the original theme. Only window decoration is restored with this step. The icons of eg. documents, pictures still carry the gnome-style layout with non ambiance icons...
See the other 2 screenshots for more details.

When I log-off and on again, its fixed, without making any changes...

I "think" issue 2 most likely appears when I start my notebook in battery mode. With power attached, I cant recall I faced that issue before... but Im not sure though

Does anybody know how to fix this?

Thanks in adavance;)

---

### Post by mcduck on 2011-03-14
For the issue no.1, that's by design, not a bug. The menus in Gnome are not supposed to show icons for every item any more, only for the most relevant items.

If you want to change that and use icons for everything, open gconf-editor, browse to desktop/gnome/interface and enable the "menus_have_icons"-key.

Can't say much about the second problem, perhaps try executing 2gnome-settings-daemon" when that happens to see if it helps?

---

### Post by gofurygo on 2011-03-14
McDuck

Just to make sure we are talking about the same menu/symbols. I added an updated screenshot of the system drop-down menu, highlighting "missing" icons.

Like said before, if I right-click on the panel --> edit menu --> scroll down until <System> it shows assigned icons named: 
preferences-desktop.svg
preferences-system.svg

So they are "there"... just not showing when I click "System" in the menu-panel.

Thanks for the 2nd issue reply, will give it a go next time that happens;)

---

### Post by rvchari on 2011-03-14
> **gofurygo said:**
> Hello

For quite a while now I have some issues with the menu panel and the window appearance. Better said, with its frequent "automated" change :(

Overall, there are 2 issues I would like to address in this post:
1) No icons being displayed in <System> menu from main panel
2) Randomly switching to Gnome-Icon-Set and/or theme on startup

1) The System drop-down menu doesnt show any icons at all and I wonder why. I went to edit the menu to check those entries but there, the icons are shown and assigned to the first 2 entries of the <System> menu. For some reason they wont show in the main panel menu --> see screenshot System_menu.png

2) Recently, when starting up Ubuntu, the desktop theme changes by itself, sometimes. Im getting some Gnome-Style desktop theme although I shut down the computer with Ambiance last time. As soon as I go to <Appearance>, _without_ re-selecting the Ambiance theme (just open the appearance dialog), it jumps back to the original theme. Only window decoration is restored with this step. The icons of eg. documents, pictures still carry the gnome-style layout with non ambiance icons...
See the other 2 screenshots for more details.

When I log-off and on again, its fixed, without making any changes...

I "think" issue 2 most likely appears when I start my notebook in battery mode. With power attached, I cant recall I faced that issue before... but Im not sure though

Does anybody know how to fix this?

Thanks in adavance;)
first, follow this thread...
[http://ubuntuforums.org/showthread.php?t=1575703]("http://ubuntuforums.org/showthread.php?t=1575703")


next... see if you can find your theme after you delete the dot nautilus (.nautilus) folder from your home directory and log out and re-log in.

the above thread will throw a lot of light on helping u solve ur problem

---

### Post by mcduck on 2011-03-14
> **gofurygo said:**
> McDuck

Just to make sure we are talking about the same menu/symbols. I added an updated screenshot of the system drop-down menu, highlighting "missing" icons.

Like said before, if I right-click on the panel --> edit menu --> scroll down until <System> it shows assigned icons named: 
preferences-desktop.svg
preferences-system.svg

So they are "there"... just not showing when I click "System" in the menu-panel.

Thanks for the 2nd issue reply, will give it a go next time that happens;)
Yes, we are talking about the same icons. They are not even supposed to appear on any recent Gnome version. Same goes for many icons in the different application menus.

Enabling the gconf key I mentioned will force them to show.

edit: From the [Gnome 2.28 release notes]("http://library.gnome.org/misc/release-notes/2.28/"):
> GNOME menus and buttons have been standardised across all applications to not display icons by default. Menu items with dynamic objects, including applications, files or bookmarks, and devices are the exception and can display an icon. This change will standardise the look and feel of menus and present a cleaner interface to users.

---

### Post by gofurygo on 2011-03-14
> Enabling the gconf key I mentioned will force them to show.Thanks McDuck, that did the trick ;)


rvchari & mcduck:
I added the gnome-settings-daemon to start-up applications. I tried to reproduce the theme error by shutting down, unplugin the notebooks charger and boot up again. No "Luck" so far... which, in this case is good :D

I will try a few more times, then mark this thread as solved if the fix remains to work...

Cheers

---

### Post by gofurygo on 2011-03-15
rvchari

I read through the thread you posted.

Like said before, I added the gnome-settings-daemon at start-up. But this morning, the bug was back. I didnt want to fiddle around with some delay scripts, so I tried your advice of deleting the .nautilus folder and I have to say, so far (after 5 reboots) the bug hasnt been back yet. I always tried to log in quickly after the login-prompt (some guys in the other thread said, waiting a while before logging in gives them a higher chance without bug). So until now, everything is fine :-) Will keep an eye on that, if it remains to be solved, I will post in the other thread again to emphazise this kind of fix.

Did you have the theme bug again after deleting the .nautilus folder or has this fix been permanent for you?

---

