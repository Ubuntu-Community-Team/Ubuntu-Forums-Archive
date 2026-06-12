---
title: "Jaunty, Display preference dialog does not show any options"
date: 2009-05-08
forum: General Help
---

### Post by thornate on 2009-05-08
I just installed Jaunty and if I go to System -> Preferences -> Display, the dialog appears but is blank. What's more, the entire computer slows down; I can't close the dialog normally but even if I kill it via the System Monitor, the computer remains sluggish until I restart.

In a different but possibly related issue, I have tried using the ATI Catalyst Control Center (comes with the hardware driver) to change the screen resolution (it's set on a default 1280X1024, which is too high for my monitor). When I select a different resolution and click OK or Apply, it pops up the dialog asking whether I want to keep the settings, but nothing has actually changed. 

I would love it if someone were able to tell me how to fix the Display dialog. If that's not possible, can someone please  give me another way to change the screen res?

---

### Post by thornate on 2009-05-09
*bump*

Is there any way to change the screen res using the shell?

---

### Post by mkngama on 2009-07-21
looks like your /etc/X11/xorg.conf is corrupted.

run the sudo  dexconf  to reset the /etc/X11/xorg.conf
Then your display preferences applet should work fine.

---

### Post by betaparadogma on 2009-07-28
the 

sudo dexconf

command does not solve the problem for me. instead the system does not show the ubuntu desktop anymore after reboot. screen is complete garbage now. 

i suppose i will reinstall now... :(




**search terms**: dual heading, two monitors, issue, problem, display properties, display property, display, monitor, screen, slow, menu, missing, not showing, not show up, ubuntu 9.04, english, dell, ati 2400 xt, dual head

---

### Post by dgrafix on 2009-08-12
Having exactly the same problem. Same card everything.

You do not need to re install, use Ctrl+Alt+F1, log in and look at the xorg.conf, there should be backup copies of it. "cp" the last one over the current one.
(comands you may not know but will need): 
cp =copy 
cd =change dir (go to /etc/X11/)
ls -la = show files with full info (like dates)

---

### Post by dgrafix on 2009-08-12
Got a fix for you / anyone else.

It seems to be a problem when the proprietry ati fglrx driver is active.


FIRSTLY TRY:
the ctrl alt F key trick mentioned below when display box "crashes".

OTHERWISE:
1- remove the ati driver. From system>admin>hw drivers
2- run dexconf  (step 1 s important here otherwise you will break it)
3- reboot
4- re-activate ati fglrx driver. From system>admin>hw drivers
5- go to display settings, (if it crashes here see below!)
6- untick mirror DO NOT CLICK DETECT DISPLAYS! 
7- arrange screens and apply.

Now here is the trick, the PC will slow down and the window will go blank.

Press Ctrl+Alt+F1 wait 3 seconds and then ctrl+alt+f7  to jump back in. (it is possible it could be f6/f8 too occasionally if more than 1 user logged in) You may need to do this a few times throught the process..
You should now be able to accept the changes and..

voila. dual head.

This ctrl+alt+F1/F7 trick may have worked in the first place (cannot confirm), so try that first!

:lolflag:

---

