---
title: "Tab Detaching in Hardy's gnome-terminal?"
date: 2008-07-10
forum: Desktop Environments
---

### Post by ph8 on 2008-07-10
Has anyone found it easier to accidentally detach tabs in the gnome-terminal app recently? 

It's really annoying me - i keep managing to 'snap off' tabs i'm working on and can't seem to turn it off!

---

### Post by artichoke on 2008-09-01
Get on to upstream about it: [http://bugzilla.gnome.org/show_bug.cgi?id=529908](http://bugzilla.gnome.org/show_bug.cgi?id=529908)

Maybe if enough people complain....

---

### Post by dirgeprat on 2008-09-18
YES!  This is totally annoying me.  Any time I click the title bar I seem to detach the tab.

I notice in the Tabs menu that you can manually detach a tab, but there is no option to re-attach it to the previous terminal!

DP

---

### Post by mmarechal on 2008-10-23
There is a workaround for reattaching a tab. Open up another tab in
the terminal you just detached and drag the first tab back to the window it came from.

---

### Post by mmarechal on 2008-12-04
Hmm, it seems like the guys developing gnome-terminal/gtk are taking their time.

As a temporary and dirty fix, you could download the source of gnome-terminal and turn off mouse tab detaching manually by editing the code.
The downside of this method is that you will not be able to update gnome-terminal anymore
or, if you do, you must redo the steps outlined below.

The following works for my current version of gnome-terminal (2.22.1).

Download source using the instructions in [http://ubuntuforums.org/showthread.php?t=48806](http://ubuntuforums.org/showthread.php?t=48806), in this case:
Download all packages required to compile gnome-terminal:
```
sudo apt-get build-dep gnome-terminal
```
Make a directory to put the source in and go there
```
mkdir -p ~/src/gnome-terminal
cd ~/src/gnome-terminal
```
Download the source code to the current directory. (You need to check the "source code" option in software sources, to be able to download source code.)
```

apt-get source gnome-terminal
```

Change directory to the new directory that was created (gnome-terminal-x.x.x).
Then edit src/terminal-window.c find the function call that reads:
```
 gtk_notebook_set_tab_detachable (GTK_NOTEBOOK (window->priv->notebook),
                                   GTK_WIDGET (screen),
                                   TRUE);
```
change it to
```
 gtk_notebook_set_tab_detachable (GTK_NOTEBOOK (window->priv->notebook),
                                   GTK_WIDGET (screen),
                                   FALSE);
```

This is the only change in the source code required to put the mouse detaching off. DON'T CHANGE ANYTHING ELSE, unless you know what you're
doing. If something went wrong you can just delete everything in the ~/src/gnome-terminal directory and start over.

To compile use the usual ./configure--make--make install routine.
Run
```
./configure
```
It will print a lot of "checking for bla bla... yes/no/whatever" lines followed by some information. There should be no errors or warnings! Otherwise, don't continue.
Type
```
make
```
Again there should be no errors (warnings are ok).
Test your new gnome-terminal (the binary is in src/gnome-terminal if everything went ok). If there are any other gnome-terminals open type
```
src/gnome-terminal --disable-factory
```
to avoid reusing your old (and thus detaching terminals).
If everything is ok type
```
sudo make install
```
to install the gnome-terminal over your old installation.

Close all terminals, to avoid reusing the old terminals the next time you open a new terminal. Now you should have a gnome-terminal that does not
detach windows using the mouse. You can still detach them using the tabs>detach menu button.

---

### Post by slidersv on 2009-02-23
> **mmarechal said:**
> There is a workaround for reattaching a tab. Open up another tab in
the terminal you just detached and drag the first tab back to the window it came from.

This is a nice workaround, but I would really like to disable detaching altogether. The code change is not an option at this time, since I have to work and not think about other stuff. I'd go for a package install at most :)

---

### Post by andre.klapper on 2009-03-10
> **artichoke said:**
> Get on to upstream about it: [http://bugzilla.gnome.org/show_bug.cgi?id=529908](http://bugzilla.gnome.org/show_bug.cgi?id=529908)

Maybe if enough people complain....

Please don't add useless "Me too" "Oh yeah fix this" comments. If people will do this too often I might disable such user accounts in GNOME Bugzilla.
GNOME Bugzilla is a bugtracker and not a wishlist or forum. Keep it clean. Come up with a fix if you want to help, but please don't spam my mailbox with such bug spam.
In fact "me too" comments are quite demotivating for developers.

---

### Post by jeffco on 2009-08-12
> **andre.klapper said:**
> Please don't add useless "Me too" "Oh yeah fix this" comments. If people will do this too often I might disable such user accounts in GNOME Bugzilla.
GNOME Bugzilla is a bugtracker and not a wishlist or forum. Keep it clean. Come up with a fix if you want to help, but please don't spam my mailbox with such bug spam.
In fact "me too" comments are quite demotivating for developers.
Hey, Andre - ME TOO!  This is a usability bug, not a feature request.  This annoys the crap out of me, too, and the more people the chime in the better.

I'm off to investigate whether I can install konsole under Gnome.  ETA: yep, it's as easy as "apt-get install konsole" - hooray!

---

### Post by redbeardmcg on 2009-08-27
Hey Jeffco, your snide response to Andre is quite obnoxious, did you forget that you got this software free of charge, with full freedom to modify to your liking? 

These developers spend quite a lot of time on these projects without getting anywhere near the level of appreciation they deserve, and people like yourself should quite honestly just go out and pay for something if what you really would like is to a: demand a feature, b: not do any work at all, c: act like an arrogant punk to the developer.

Take a hike.

> **jeffco said:**
> Hey, Andre - ME TOO!  This is a usability bug, not a feature request.  This annoys the crap out of me, too, and the more people the chime in the better.

I'm off to investigate whether I can install konsole under Gnome.  ETA: yep, it's as easy as "apt-get install konsole" - hooray!

---

