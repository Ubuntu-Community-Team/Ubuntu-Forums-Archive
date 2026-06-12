---
title: "Downloader for X quits immediately"
date: 2005-08-31
forum: Desktop Environments
---

### Post by firefly2442 on 2005-08-31
When I try running Downloader for X it pops up for a moment and then immediately quits.  Is this a bug or maybe a dependency problem perhaps?

---

### Post by jasmuz on 2005-08-31
Delete the .d4x directory in your /home directory to see if it does any better.

---

### Post by firefly2442 on 2005-08-31
Hmm.... I don't have that directory.  Should I try creating it?

---

### Post by firefly2442 on 2005-08-31
When I try running it from the commandline it says "segmentation fault".....

---

### Post by firefly2442 on 2005-09-01
I tried creating the directory and it still doesn't seem to work...

---

### Post by jasmuz on 2005-09-02
I would recommend you reinstall d4x

---

### Post by firefly2442 on 2005-09-03
I tried apt-get removing it and reinstalling it.  Didn't seem to work.  Is it possible that different dependency software that it needs and their versions could be incompatible?

---

### Post by tweak on 2005-09-05
[QUOTE=firefly2442]I tried apt-get removing it and reinstalling it.  Didn't seem to work.  Is it possible that different dependency software that it needs and their versions could be incompatible?[/QUOTE]
 I was having the same problem for a while. Turns out that d4x doesn't like some window control themes - try changing your theme and see what happens

---

### Post by firefly2442 on 2005-09-05
WOW.  That was it.  Thank you so much! :)

---

### Post by telmo on 2005-11-04
I have a problem just like that... Segmentation fault and everything, but my problem isn't solved by changing the theme... :S

Any ideas? I've Uninstalled it and Re-installed it and it just doesn't work... i have also tried every theme available, and no can do!

Can anyone solve this? Or maybe suggest another download manager, perhaps...

thx

---

### Post by jrib on 2005-11-04
[QUOTE=telmo]I have a problem just like that... Segmentation fault and everything, but my problem isn't solved by changing the theme... :S

Any ideas? I've Uninstalled it and Re-installed it and it just doesn't work... i have also tried every theme available, and no can do!

Can anyone solve this? Or maybe suggest another download manager, perhaps...

thx[/QUOTE]

did you just change the theme to a different theme?  IIRC there were several that did not work, but clearlooks was one that it worked on.

---

### Post by telmo on 2005-11-05
Yep... Like i said before, i tried every theme available...

---

### Post by jrib on 2005-11-05
[QUOTE=telmo]Yep... Like i said before, i tried every theme available...[/QUOTE]

ah sorry, missed that somehow...

You can try [aria]("http://aria-rpm.sourceforge.net/") and [gwget]("http://gnome.org/projects/gwget/") (I use gwget but it isn't feature rich, just a simple download manager).  Both are in the repos.

---

### Post by telmo on 2005-11-05
WGet is nice and simple, just as i like it... (Why didn't i search for a download manager in synaptic before?)

Thank you.

---

