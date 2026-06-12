---
title: "Community themes - this feels like a lame question"
date: 2010-09-03
forum: Desktop Environments
---

### Post by discodonkey on 2010-09-03
I have been using Linux off and on for several years and I feel like I have have a good grasp on what to do and what not to do.  However, I have never really played with it visually.  Now that it is my full-time OS, I want to pretty it up to my taste.

I installed the community themes via the sudo install command, the themes are in the themes folder, but, when I go to the themes tab to apply one, they are not listed.  What have I missed?

Thanks,

---

### Post by quixote on 2010-09-05
I don't know the specific answer to your question, but this may be the general issue:  "sudo install" is a purely command line operation.  It doesn't necessarily integrate with the GUI gnome desktop unless the installed package itself does that at the end.  Sounds like the themes don't if you install them that way.  

I see that synaptic has the option to install community themes.  If it were me, I'd just go ahead and try that and everything will probably magically work. :D  (If you're the cautious type, uninstall first from the command line the same way you installed, but with something like themes, I doubt it's a big deal.)

---

### Post by discodonkey on 2010-09-10
Thanks.  I think something didn't go right.  I am going to reinstall them via synaptics manager and see if that does it.

---

### Post by urukrama on 2010-09-10
> **quixote said:**
> I don't know the specific answer to your question, but this may be the general issue:  "sudo install" is a purely command line operation.  It doesn't necessarily integrate with the GUI gnome desktop unless the installed package itself does that at the end.  Sounds like the themes don't if you install them that way.

> **discodonkey said:**
> Thanks.  I think something didn't go right.  I am going to reinstall them via synaptics manager and see if that does it.

If you used the right command (it should have been *sudo apt-get install community-themes* or *sudo aptitude install community-themes*), that should absolutely make no difference. Synaptics and apt-get both use the same underlying tools to install applications. It is not the case that you can only install command-line applications from the command-line. What is the exact command you used? The themes should normally come up in the themes dialog, and if they are installed, they will be located in /usr/share/themes/

You can also download themes from websites like [gnome-look.org]("http://gnome-look.org"). You don't need to be using sudo to install those. Just extract the theme file archive you've downloaded and copy it to your /home/USERNAME/.themes folder (create that if it doesn't exist).

---

