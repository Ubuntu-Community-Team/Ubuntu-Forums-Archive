---
title: "How do I upgrade"
date: 2009-04-15
forum: General Help
---

### Post by Mark_in_Hollywood on 2009-04-15
It's almost time again for a new Ubuntu release and I cannot find a How-To that shows me how to backup what I have. And by that I mean:

OS
Installed Applications
Configuration files
saved data, e.g., mp3 files, word-processor docs, etc.

I would prefer to do a clean install of the OS, but cannot figure out a method of restoring the applications (Adobe Reader for example), and having all the pieces connect and work correctly.

Is there a method to do this?

By the bye: rsync won't do a perfect backup as it bumps a few files, such as: .gvfs - so I cannot simply do a restore.

If you know how to get rsync to ignore or skip the root-owned files in /home, please let me know.

Thanks, community.

---

### Post by bodhi.zazen on 2009-04-15
Easiest way it to follow the directions on the wiki :

```
gksu update-manager -d
```[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

The other option, and what I do, is to make a data partition. The data partition is preserverd if you do a fresh install.

I personally do not care about most the config or . files in $HOME. The ones I do care about (.bashrc) I copy to the data partition.

---

### Post by wolfen69 on 2009-04-15
if you don't mind reinstalling applications, the best thing to do is to go to your home folder and do Ctrl-H. this will show you the hidden configuration files. save which ones you want to a pendrive or something. the same with mp3's. just put them on another drive. then do a clean install and put everything back. works for me every time.

---

### Post by mckenna1977 on 2009-04-15
try having a look at partimage.org

as far as i can tell you can create an iso image of your system but this won't do it just for data. for backing up bits of your system you could try bacula

for cleaning and upgrading to a new system why don't you just apt-get remove and apt-get purge what you know is installed but you don't want then apt-get autoclean what's installed but is orphaned then apt-get dist-upgrade or change your version in /etc/sources.list and then update

---

### Post by mb_webguy on 2009-04-15
You do know you don't have to do a clean install of a new version, right?  Update Manager can upgrade you to the new version just as it updates new packages.  Just make sure that in Software Sources, on the Updates, at the bottom where it says "Show new distribution releases" that you have "Normal releases" selected.

---

