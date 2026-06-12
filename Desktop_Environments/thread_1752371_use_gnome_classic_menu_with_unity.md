---
title: "use gnome classic menu with unity"
date: 2011-05-07
forum: Desktop Environments
---

### Post by curbuntuforums on 2011-05-07
I'd give this unity thing a chance if I didn't have to keep wasting clicks "opening up" the darned menu!!  

Q: Can I use the classic gnome start menu with unity?

---

### Post by mc4man on 2011-05-07
> Q: Can I use the classic gnome start menu with unity?
If you wish - 2 ways
Log into unity, start gnome-panel (I think it's silly but you can do so

Log into Classic, remove top panel, put your gnome-menu applet on the bottom or a right side panel, then enable the unity plugin in ccsm

=================================================

Or just use unity and add menus to the launcher - icon = category, quicklist = menu

---

### Post by Frogs Hair on 2011-05-07
I started the gnome panel in unity via the terminal just to check it out. When the terminal is closed the panel is removed and it is , of course , the bottom panel.

---

### Post by curbuntuforums on 2011-05-07
thanks
1st helped flesh out launcher but quickly became silly, you're right
2nd well... maybe for temporary things, but clutters what unity is trying to clear up
3rd - add menus to launcher?

---

### Post by mc4man on 2011-05-07
> **curbuntuforums said:**
> 
3rd - add menus to launcher?
I have several examples in this thread, (posts 29,34,36) they are very easy to create once you get the idea
They are not 100% suitable for C&P, more to show how.

If you wish to try but don't get the deal, post a category and a list of what you want in it, I'll make you one to start.

[http://ubuntuforums.org/showthread.php?p=10778758#post10778758](http://ubuntuforums.org/showthread.php?p=10778758#post10778758)

---

### Post by Frogs Hair on 2011-05-07
The applications launcher on the panel offers access to all the items that were on the menus . A good shortcut to have is the system settings as a launcher because it has everything that was on the administration and preferences menu .

---

### Post by curbuntuforums on 2011-05-07
'system settings' app in launcher relieves some transition pain, for sure
and
those quicklist menus look very slick
thnx

---

### Post by Copper Bezel on 2011-05-07
> I started the gnome panel in unity via the terminal just to check it out. When the terminal is closed the panel is removed and it is , of course , the bottom panel.

Unless it's a daemon, any process will generally die when you close the terminal session. You can preface any command with [font="Courier New"]setsid[/font] to prevent this. Gnome Panel can also be launched from the Run Dialog.

While the Gnome Main Menu (or clones such as Cairo Menu, used in Cairo Dock and AWN) requires a panel to attach to, other close equivalents do not. For instance, you might look into [Cardapio]("https://launchpad.net/cardapio"), which can be invoked by the command cardapio --show-near-mouse, which you could use as the exec line in a Launcher icon as described above.

But yes, the category buttons are certainly prettier.

---

### Post by mc4man on 2011-05-07
> I'd give this unity thing a chance if ....
Ultimately I'd think it will be the upcoming O release that will give the best indication of where unity is heading. It wouldn't surprise me if there were some changes of note that may change  minds _either_ way.
(I've had a great time w/ it for the last 6 months and really like  using, but there is the possibility that I could feel differently come 11.10.

---

