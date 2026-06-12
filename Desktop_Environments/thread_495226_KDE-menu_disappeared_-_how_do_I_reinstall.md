---
title: "KDE-menu disappeared - how do I reinstall?"
date: 2007-07-07
forum: Desktop Environments
---

### Post by RipRapRob on 2007-07-07
I tried installing Kickoff Kicker, but didn't like it (I only wanted the 'search' feature).

So I uninstalled it.

But now I have NO KDE-menu and no menu bar, and no clock and no.... :(

How do I reinstall KDE/make KDE re-appear?

I'm using KUBUNTU, newest version, and would like to avoid having til reinstall KUBUNTU (and loosing my data).

Please help a Newbie! :(

I've tried reinstalling from the terminal, and it says DONE, but the menu is not shown.

/Rob

---

### Post by RipRapRob on 2007-07-07
I should add: I can choose KDE from the start-menu, but to no avail :(

/Rob

---

### Post by kugn on 2007-07-08
you might want to 
sudo apt-get install kubuntu-desktop
This would install any other missing parts to your kubuntu installation.

if that doesn't help, then run
kcontrol
where you should look for 'panels' under 'desktop'. see if you can add a panel there to your desktop.

good luck :)

---

### Post by RipRapRob on 2007-07-08
Thank your for your help.

I couldn't get it to work, so I re-installed ](*,)](*,)](*,)

But thanks again!

/Rob

---

### Post by mermshaus on 2007-07-10
This piece of advice I found on [kde-apps.org](http://www.kde-apps.org/content/show.php?content=50240&forumpage=2) worked for me (Kubuntu Feisty):

```
dpkg --purge kicker-kickoff
apt-get install --reinstall kicker
```

You just have to reconfigure your kicker settings.

---

