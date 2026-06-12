---
title: "Synaptic quick search doesn't working!"
date: 2009-04-10
forum: Desktop Environments
---

### Post by adamitj on 2009-04-10
I did a new fresh installation of Ubuntu 8.10 x64 into my notebook. I noticed a strange problem on Synaptic: the quick search is not working more!

To check it out, I scrolled down the package list without any parameter search, and found "celestia" package perfectly. When I type "celestia" into quick search, no package is found.

Maybe this is a synaptic error? Or maybe there is some new way to search for packages?

---

### Post by adamitj on 2009-04-10
Here are the prints

---

### Post by Chemical Imbalance on 2009-04-10
> **adamitj said:**
> I did a new fresh installation of Ubuntu 8.10 x64 into my notebook. I noticed a strange problem on Synaptic: the quick search is not working more!

To check it out, I scrolled down the package list without any parameter search, and found "celestia" package perfectly. When I type "celestia" into quick search, no package is found.

Maybe this is a synaptic error? Or maybe there is some new way to search for packages?

Quick search only works for searching the currently displayed list, not searching the whole datebase of packages--Search is for that.

For instance, click on "installed packages".  A list of your installed packages will show.  Quick Search only looks through those listed packages.
Use Search to find something from the whole database.

---

### Post by adamitj on 2009-04-10
> **Chemical Imbalance said:**
> Quick search only works for searching the currently displayed list, not searching the whole datebase of packages--Search is for that.

For instance, click on "installed packages".  A list of your installed packages will show.  Quick Search only looks through those listed packages.
Use Search to find something from the whole database.

I have to disagree with you. I always used quick search to select and install packages of *all* packages. For example, when I typed the string "sun java jdk" (without quotes) into quick search field, Synaptic brings me a list of packages where I used to select sun-java6-jdk.

Now using it on "installed packages" it brings me a a list of non-relative packages with the same search parameter.

For a while I'll be using the search button. But I think this is a bug, or at least a behavior change.

---

### Post by Paranoid Tux on 2009-04-10
It is a problem that I have been having too, so maybe it should be reported as a bug and see where it leads. It could well be that the developers had a good reason for the change or that it was just a oops.

Paranoid

---

### Post by Chemical Imbalance on 2009-04-10
> **adamitj said:**
> I have to disagree with you. I always used quick search to select and install packages of *all* packages. For example, when I typed the string "sun java jdk" (without quotes) into quick search field, Synaptic brings me a list of packages where I used to select sun-java6-jdk.

Now using it on "installed packages" it brings me a a list of non-relative packages with the same search parameter.

For a while I'll be using the search button. But I think this is a bug, or at least a behavior change.

That's never what I've noticed.  Its never worked that way for me.

---

### Post by santa17 on 2009-04-21
Same problem here.
Installed Kubuntu 8.10 2 days ago. 
When trying quick search on "all" the search does not work. 
After typing few letters, it displays no results, even though the package positively was in the list before.

When running form konsole, following error pops out:
> (synaptic:18691): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

And I'm having problems with adept as well. Adept can't find almost any packages. 

Any ideas?

Thanks

---

### Post by adamitj on 2009-04-21
Suddenly, the problem disappears. I could notice a message at the label where says "Quick Search" switched to "Rebuilding Index". I wait this message disappears, and since then everything back to normal.

---

### Post by adamitj on 2009-04-21
> **adamitj said:**
> Suddenly, the problem disappears. I could notice a message at the label where says "Quick Search" switched to "Rebuilding Index". I wait this message disappears, and since then everything back to normal.

Oh. I forgot to mention. The "Rebuilding Index" appeared after run in console:

```
sudo aptitude update
```

---

### Post by MadCow108 on 2009-04-22
this helped when I had the same problem:
[http://ubuntuforums.org/showthread.php?t=964232&highlight=synaptic](http://ubuntuforums.org/showthread.php?t=964232&highlight=synaptic)
> 
yeap i did too but

Michael Vogt suggested to do "sudo update-apt-xapian-index" and restart Synaptic, which does help.

from

[https://bugs.launchpad.net/ubuntu/+s...ic/+bug/288797](https://bugs.launchpad.net/ubuntu/+s...ic/+bug/288797)


---

### Post by santa17 on 2009-04-23
I did 
```
sudo update-apt-xapian-index
```
and it works perfectly now.

Thanks

---

### Post by adamitj on 2009-04-23
> **santa17 said:**
> I did 
```
sudo update-apt-xapian-index
```
and it works perfectly now.

Thanks

Me too. I was experiencing the same problem at home, in my notebook. Now everything is fine.

---

### Post by Richard0612 on 2009-04-26
I had the same problem on 9.04 (didn't happen on the beta though, strange), and running the update-apt... command didn't help.

However, I ran 
```
gksudo nautilus
```and removed the '/var/lib/apt-xapian-index' folder completely (you could do this from the terminal, if you prefer). After then rerunning the update command, in essence forcing the index to be updated, synaptic seems to work fine.

---

