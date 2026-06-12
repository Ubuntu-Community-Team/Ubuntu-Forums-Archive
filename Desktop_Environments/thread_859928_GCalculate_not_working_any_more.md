---
title: "GCalculate not working any more"
date: 2008-07-15
forum: Desktop Environments
---

### Post by lviggiani on 2008-07-15
Hi,
I've been using gnome-do with gcalculate plug in for a while and everything was working well. Suddenly, few days ago, gcalculate plugin stopped working. Whatever I type (i.e. 1+2) I always get the message "Google calculator could not evaluate the expression".
I've tryed uninstalling and re installing the gnome-do-plugins package but nothing changed.
Anyone can help me please?
Thanks.

---

### Post by Mandrake12 on 2008-08-10
write the following in a terminal to purge gnome-do settings, worked for me: rm -rf ~/.local/share/gnome-do

---

### Post by 1jackjack on 2009-05-14
I know this is old, but I have exactly the same problem. Not on Jaunty, with gnome-do v0.8.1.3 from the repos.

I tried killing gnome-do, then the following, but nothing works :(
rm -rf ~/.local/share/gnome-do

---

### Post by 1jackjack on 2009-05-22
Update: I heard that the latest version in the repos had fixed this bug, and it's true (it worked for me, on jaunty anyway). You can get instructions on how to checkout a copy and compile it from source here:
[http://do.davebsd.com/wiki/index.php?title=Installing_Do#From_Source](http://do.davebsd.com/wiki/index.php?title=Installing_Do#From_Source)

---

### Post by asmoore82 on 2009-05-22
> **Mandrake12 said:**
> write the following in a terminal to purge gnome-do settings, worked for me: rm -rf ~/.local/share/gnome-do

I recommend renaming it to a backup location because "you never know" what could go wrong ...

```
mv ~/.local/share/gnome-do ~/.local/share/gnome-do.backup
```

---

### Post by Cuco3 on 2009-12-16
> **1jackjack said:**
> Update: I heard that the latest version in the repos had fixed this bug, and it's true (it worked for me, on jaunty anyway). You can get instructions on how to checkout a copy and compile it from source here:
[http://do.davebsd.com/wiki/index.php?title=Installing_Do#From_Source](http://do.davebsd.com/wiki/index.php?title=Installing_Do#From_Source)thanks, I was looking for a fix to this problem.

---

