---
title: "Nautilus menu bar dissapeared, right-click disabled"
date: 2008-07-28
forum: Desktop Environments
---

### Post by CFBauer on 2008-07-28
Hello,

As the title implies, my menu bar and shortcuts in nautilus have disappeared.  I've used gconf-editor to check the nautilus preferences, and have ensured that "start_with_toolbar" is ticked.  I have also tried restarting nautilus runnig "nautilus" in the terminal, to no avail.

Also, right clicking on nautilus windows and the desktop is not responding.  I think this could be related.

I have attached a screen to demonstrate what's going on.  If anyone has a suggestion I would appreciate your help.

Thanks for reading.

-Chris

---

### Post by CFBauer on 2008-07-29
shameless bump

---

### Post by jediborger on 2008-07-29
Well this is an interesting issue. You might want to try removing the nautilus package and purging the config files. You can use Synaptic and select the option for complete removal or use the following command:
```
sudo apt-get --purge remove nautilus
```
Then you'll want to install nautlius again. Post back with your results.

---

### Post by CFBauer on 2008-07-29
Thanks for your help jediborger.

I went ahead and removed nautilus using your command, then reinstalled with a "sudo apt-get install nautilus".  

After a logout then login, still no dice.  No menu bar, no right click.

I always seem to get the "interesting" issues ;).

---

### Post by jediborger on 2008-07-29
Hmm. Have you tried deleting your .nautilus directory in your home directory. You can use ctrl+h to show hidden stuff since you can't use the menus. Or ls -a if you're feeling some command line goodness.

---

### Post by CFBauer on 2008-07-29
Unfortunately, deleting the contents of .nautilus didn't help either.  My desktop icons are rearranged :), but no luck displaying a menu bar.

Thanks again for your help.

---

### Post by CFBauer on 2008-07-30
I've temporarily switched to Dolphin.  :)

---

### Post by ironwolfe on 2008-10-04
I am having the same issue - any resolution?

---

### Post by alex69 on 2009-04-21
mee too, the same problem but with a new feature : both nautilus and the terminal stop showing the menu bar, no way to make them show again

---

### Post by hannosiegers on 2009-05-01
I had the same problem.
Turned out i had Global Menu Panel Applet installed and in there I activated Enable Global Menu for GTK applications.
Ticking it off did the trick.
(Add to panel->add Global Menu Panel Applet, rightclick for preferences)

---

### Post by SteveHillier on 2009-05-05
I don't know if this is the same issue, but I have lost the 'minimse', 'restore' and 'maximise' buttons from the menu bar.  Also in windows that are not full screen I have lost the border.
I did not notice this until AFTER I have changed the menu in Firefox to display the 'New Tab' icon, but that does not mean to say it wasn't broken before then.
Version is Jaunty - 9.04

---

### Post by SteveHillier on 2009-05-06
No.  Not my problem at all.
I did a rebuild.  I then downloaded the nvidia drivers so that I could read my screen in 1280 x 1024.  I overwrote xorg.conf and blow me down with a feather (or words to the same effect) I lost my icons again.
Can't stop, I'm off to repair xorg.conf!!!!!!!!!!!!!
Steve

---

### Post by chefev on 2009-08-19
I had the right-click/no desktop icons problem for a while too. For me the solution was maddeningly simple.
Somehow it seems that Nautilus got removed from the Startup Applications list. Re-add it.
Done.
Now the right-click menu works and the desktop icons show up again.

---

### Post by VoSi on 2009-09-27
try to downgrade then restart x

---

### Post by flamepanther on 2009-09-28
I encountered this issue.  For me, at least, it seems to be related to two things:

1. The toolbar is visible (regardless of toolbar setting in gconf!) as long as the navigation bar is disabled in gconf. Enable the navigation bar, and the toolbar goes away.  Sidebar and status bar seem to have no effect.

2. The issue only occurs after a recent Nautilus update. Only package version "nautilus_2.26.2-0ubuntu4" exhibits the problem.  Downgrading to nautilus_2.26.2-0ubuntu2 returns the menu bar behavior to normal.  I hadn't read this topic yet, so I hadn't seen VoSi suggest it, but basically his suggestion works.

I do NOT have the gnome global menu installed.  For the time being, I will be locking the version to nautilus_2.26.2-0ubuntu2 on my system.  Any input on what might be going wrong here?

EDIT:
Since CFBauer posted his original problem over a year ago, I doubt his issue was the same as mine.:confused:

EDIT 2: The version that caused my problem seems to have come from a PPA I've been using.  Looks like I'll be disabling that one.

---

### Post by Locoxella on 2009-09-30
Got the same problem. Im also get a failed nautilus from a ppa repository. Presumably, gloobus repos.

Im having problems to switch back to the normal ubuntu version with out making a mess.

---

### Post by Xan63 on 2009-09-30
Hi,
I'm experiencing the same strange bug: since i've made nautilus updates, I can't have a nautilus windows with both the gconf options "start with location bar" and "start with side bar".

Do you have any idea about how could we solve this problem? how could we downgrade to the last nautilus version?

Thanks of a lot for any help :)

---

### Post by ammonkey on 2009-09-30
Hi, there were a nasty bug about the gconf parameters (start_with_toolbar). A fix has been committed it's a question of hours before the next ppa update.

for more informations: [https://answers.launchpad.net/gloobus/+question/84080](https://answers.launchpad.net/gloobus/+question/84080)

---

### Post by thomassisson on 2013-04-14
I'm suspecting that the developers have removed the menu bar from Nautilus. They think we want a web app or widget instead of a full fledged application. I find this really annoying; especially since some things are simply not available in Dolphin, my preferred file manager.

---

### Post by overdrank on 2013-04-14
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

