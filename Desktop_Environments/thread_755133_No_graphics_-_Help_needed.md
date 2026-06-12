---
title: "No graphics - Help needed"
date: 2008-04-14
forum: Desktop Environments
---

### Post by skipsbro on 2008-04-14
I recently checked out KDE 3 & 4 and when I tried to uninstall them via[[COLOR="Navy"] a guide on this site[/COLOR]]("http://ubuntuforums.org/showthread.php?t=126210"), I seem to have lost all of my graphic capabilities. I can't describe what is happening because I really don't understand what went wrong, but if anyone could provide help short of re-formatting my computer, that would be great!

---

### Post by warp99 on 2008-04-14
Did you remove all of the entries in your sources.list that pointed to the kde4 programs and libraries?

Edit:
When you say graphics do you mean you login screen or your desktop?

---

### Post by skipsbro on 2008-04-15
No graphics, nothing, no login (visual anyways) and no desktop. I used apt-get to install both kde and kde4 and I've tried puring gnome and reinstalling it, that didn't work either.

---

### Post by b3nw on 2008-04-15
install kdm or gdm, this should get you to a graphical login screen. you may then have to hunt around in the options to select kde as the session you want to start.

you may be better off installing kubuntu-desktop, but this will give you alot of extra stuff. It will properly configure you to get a X session + login going though.

good luck.

---

### Post by warp99 on 2008-04-16
First run this string:
```
sudo aptitude update
```
then the following:
```
sudo aptitude install kubuntu-desktop
```
Yes that is install because we need the extra packages on the system to remove the entire kubuntu-desktop, then issue the following:
```
sudo aptitude remove kubuntu-desktop
```
that's going to remove **all** of the components of the KDE desktop, then run
```
sudo aptitude clean
```
to clean out the cache, then you want gnome back I gather from your post so do this:
```
sudo aptitude install gnome-desktop
```

If this fails to restore your gnome session then:
```
sudo aptitude remove gnome-desktop
```
then once again:
```
sudo aptitude install gnome-desktop
```

Use 'aptitude' not 'apt-get' and make sure that the repositories for the KDE4 packages have been removed from your sources.list file. If you get an error about dependencies just remove the conflicting package using aptitude and try again.

After all this is completed you can run a program called 'deborphan' that will look for packages that have no dependencies so you can remove any remaining KDE4 packages. The program is in the universe repositories.

Edit:
If your not sure what is going to happen you can use the '-s' parameter to do a simulation. Example:
```
sudo aptitude -s install kubuntu-desktop
```
will only give you the expected output, not the real thing.

---

