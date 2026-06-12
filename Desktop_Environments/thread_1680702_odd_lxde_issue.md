---
title: "odd lxde issue"
date: 2011-02-02
forum: Desktop Environments
---

### Post by kero4 on 2011-02-02
Hey,

Got a little bored a decided to do a new minimal install of ubuntu 10.10 using install command line system only.

Then went through the normal steps of installing xorg, lxde and a few other goodies life firefox, flash, etc etc.

Since I use almost no programs, I wanted LXDE with simply a few things I use and that's it. I am not new to minimal installs and have made quite a few, HOWEVER:

Here is a very odd thing I ran into, on the menu when I click the lxde icon, I have this menu listing called "OTHER" with a huge programs liste that I did not install myself, unless something went haywire.

The listing starts with "activate screen saver (next)" and ends at the bottom of this huge list with "w3m" with a whole bunch of X listings in the middle amongst other things

Now, my only real question is, what could have gone wrong AND is it possible that the fresh install picked up data from the partition that had an old linux install I had, not old per say age wise, just one I had used for a few months before I decided to play a bit.

I don't recall running into this issue with other minimals I have done and do them the same way, command line system install, the aptitude update, aptitude upgrade, install xorg, install LXDE (or other), followed up by a login manager and a few programs.

Any thoughts???

Thanks

---

### Post by Brandon Williams on 2011-02-03
menu-xdg is installed as a recommendation of lxde unless you turn off automatic installation of recommendations. It generates a lot of desktop menu entries for commonly installed programs, including w3m and xscreensaver. You could deinstall lxde, xorg, etc., turn off automatic installation of recommends, and then reinstall lxde, xorg, etc. After that, you will probably have a lot less of this extra stuff installed, and none of it will show up in your menu.

Alternatively, turn off auto install of recommends, mark everything as autoinstalled (which will mark everything for remove), and then start working your way through the list picking only the things that you actually want installed. This will pull in the dependencies of those thing, but will not pull in the recommends. When you're done, just remove the packages that you haven't selected or pulled is as dependencies. It's safer _not_ to use this approach, since you might accidentally remove things that shouldn't be removed. However, if you're very careful, you'll end up with a system on which you know that only the absolute minimum set up packages has been installed that allows you to do want you want to do.

---

### Post by kero4 on 2011-03-03
Brandon,

Is there a way for me to start from scratch from the command line system and NOT get this menu entry "OTHER" with this huge list of programs and such?

I tried again before I checked back and the exact same thing happened again, I thought maybe I did something wrong.

turn off automatic installation of recommends - can this be done while doing the command line install???

My goal is to get the command line system installed, do the usual xorg, lxde and a few other pograms WITHOUT this entry "OTHER" in the menu with this huge list.

Any help would be appreciated, I would rather do it the right way the first time.

Why does the entry "OTHER" appear with the huge list, is it some glitch or the install does not know where to put this list of programs?

---

### Post by mcduck on 2011-03-04
No,it's not a bug or a glitch, the programs are stuff that's included on the base Ubuntu setup. It's just that most of them are the kind of apps that aren't really relevant to have in desktop menus, while xdg-menu's purpose i to list every possible program you have (instead of listing programs that actually have a desktop menu files)

Even if you did a minimal Ubuntu installation you'd still have plenty of applications and tools that are not usually included in menus. Command-line text editors, programs that usually run in the background and so on. You'll have such things on pretty much any functioning operating system, now you just happen to have a menu entry that lists all that stuff.

If it helps, it's unlikely that all those together would take any meaningful amount of disk space, and most of them are stuff you actually *want* on your system, just not in your menus because you either never need to run those programs yourself, or only use them from command line. So simply removing the menu entry is probably the best way to go...

The reason for such tool as the xdg-menu is that LXDE uses Openbox, which doesn't use normal desktop menu entries and doesn't have any automatic way of adding applications into the menu, leaving all that to the user to do manually. Xdg-menu gives a simpler way to access all available applications, at least until the user has time (and skills) to configure his own menu.

---

### Post by kero4 on 2011-03-04
So is there a program I can install to let me edit the lxde menu to remove the "OTHERS" entry from the menu?

Thanks all for your help btw!

---

