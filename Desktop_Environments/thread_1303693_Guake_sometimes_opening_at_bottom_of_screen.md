---
title: "Guake sometimes opening at bottom of screen"
date: 2009-10-28
forum: Desktop Environments
---

### Post by Nevon on 2009-10-28
I'm using a drop-down style terminal application called [Guake]("http://guake.org/"). When I hit F12, it's supposed to drop down from the top, as shown in the following screenshot:

[Screenshot of Guake behaving normally](http://i38.tinypic.com/11r5g7s.png)

However, sometimes when I hit F12, Guake appears at the bottom of the screen, as shown in this mockup (I couldn't replicate it at the moment, as the problem comes and goes).

[Guake behaving badly](http://i34.tinypic.com/fbdl04.png)

It would seem the problem is related to Compiz, but I don't know what settings to even look for in the compiz config settings manager. Also, I can't for the life of me figure out why it only happens sometimes.

---

### Post by meho_r on 2009-10-28
If you think it's Compiz related, maybe to try Place plugin and put Guake to top. This is somehow ridiculous but nothing else comes in mind.

BTW, on Jaunty no problem for last 6 month. With Compiz. Maybe Karmic issue?

---

### Post by Nevon on 2009-10-29
> **meho_r said:**
> If you think it's Compiz related, maybe to try Place plugin and put Guake to top. This is somehow ridiculous but nothing else comes in mind.

BTW, on Jaunty no problem for last 6 month. With Compiz. Maybe Karmic issue?

That does seem to have solved it, although it now uses the compiz window-chango-presto animation rather than just dropping down from the top. That's something I can live with though.

Thanks for the help!

---

### Post by itmustbejj on 2009-10-29
I just started having this issue about a week ago when I upgraded to the 9.10 RC.  I'm curious what the cause could be.

---

### Post by yanaek on 2009-11-08
i think it's related to firefox, if you have firefox window opened and placed too high on your screen, Guake-Terminal starts to appear on the bottom, if you move the firefox window lower, Guake starts to appear at the top (like normal)

---

### Post by Sarki on 2009-11-14
It's a confirmed bug.

Actually the only reliable option is (found [here, thanks Jeff!]("https://bugs.launchpad.net/ubuntu/+source/guake/+bug/457654/comments/8")):

First install the CompizConfig Setting Manager ([sudo apt-get install compizconfig-settings-manager]("apt://compizconfig-settings-manager"))
And then go to **System** / **Preferences** / **CompizConfig Settings Manager**
Once there, go to the Window Management section and activate the Place plugin.
- Click on it to edit its settings.
- Go to the Fixed Window Placement tab and in the first section "Windows with fixed positions" create a rule.
[INDENT]In the text field type "class=Guake.py"
set 0 as X and Y positions
Check "keep in workarea".
[/INDENT]
Close the CompizConfig Settings Manager and that's it, solved.

---

### Post by GrumpyBob on 2009-12-14
> **Sarki said:**
> It's a confirmed bug.

Actually the only reliable option is (found [here, thanks Jeff!]("https://bugs.launchpad.net/ubuntu/+source/guake/+bug/457654/comments/8")):

First install the CompizConfig Setting Manager ([sudo apt-get install compizconfig-settings-manager]("apt://compizconfig-settings-manager"))
And then go to **System** / **Preferences** / **CompizConfig Settings Manager**
Once there, go to the Window Management section and activate the Place plugin.
- Click on it to edit its settings.
- Go to the Fixed Window Placement tab and in the first section "Windows with fixed positions" create a rule.
[INDENT]In the text field type "class=Guake.py"
set 0 as X and Y positions
Check "keep in workarea".
[/INDENT]
Close the CompizConfig Settings Manager and that's it, solved.

This didn't work for me.  Instead, inactivating the "Place Windows" plugin seemed to do the trick.

R

---

