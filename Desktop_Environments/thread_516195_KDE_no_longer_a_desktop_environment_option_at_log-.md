---
title: "KDE no longer a desktop environment option at log-on"
date: 2007-08-02
forum: Desktop Environments
---

### Post by kansas_plainsman on 2007-08-02
Well, I initially installed kubuntu - then updated it to include xfce, and until a few days ago I could, at log-on switch between the two desktop environments.

Now it get the basic ubuntu log-on splash screen, which then takes me directly to xfce - no option to select KDE.  What happened?  Is this a bug?  Is there a way to fix it?

---

### Post by pbcartwright on 2007-08-03
you might try to reinstall kubuntu-desktop or remove & install it..
sudo apt-get install kubuntu-desktop

---

### Post by kansas_plainsman on 2007-08-03
I tried uninstalling and re-installing.  No joy.  I also tried installing several other desktop environments, hoping to kick-start the process - they don't show up.

I went to the console and saw that kinit is complaining that it can't find a resume image and that things are defaulting to a default log-in.  I may have to re-install the whole system from distribution cd.  Any other options?

---

### Post by Happy_Man on 2007-08-03
No, it's not Kinit. I get the same error, and all is fine with me. Any other errors?

---

### Post by kansas_plainsman on 2007-08-14
Just to sort-of finish this thread - I never figured out how to correct the lost ui options problem - ended up re-installing from my master.  So far I've had DIFFERENT problems (mostly related to nvidia and resolutions) but I've got xfce, kde and blackbox options still with me through several log-outs and two full hardware shutdown cycles.

I generally like ubuntu, but slackware never gave me such mysterious problems.  Difference in how much the software tries to do for you, I suppose.

---

### Post by bmartin on 2007-08-14
Argh!!! If only I had been faster!!!

I believe you wanted the **sudo dpkg-reconfigure kdm**. I think the problem was that your computer switched from using KDM and that's why your login was so weird. I've been playing around trying to fix something I noticed a while back... for some reason, there are two copies of Xorg running when GDM starts. It's very annoying; they both use a lot of memory :-( Try doing a **top**, then sort by memory... maybe you have that same problem.

---

