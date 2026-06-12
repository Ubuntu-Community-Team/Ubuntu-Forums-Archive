---
title: "Gnome shell - basic questions"
date: 2010-08-14
forum: Desktop Environments
---

### Post by Warthaug on 2010-08-14
I've installed gnome shell from the repositories (I'm running ubuntu 10.04, 64bit), and have been playing with it for a bit.  I have come across a few things which in my mind should be simple to figure out, but despite several google searches I've not been able to find the answers.  I was hoping people here may be able to answer my simple questions:

1) How can I access the recycling bin?  If I delete a file it goes into the bin, as the file appears in the bin in gnome 2 after a reboot.

2) Can I get the application menu to list any way other than alphabetical?  I like having it organized by category.

3) Is there a way to go back to gnome 2, without logging out and then back in?  (i.e. shell command)?

Bryan

---

### Post by michaelaye on 2010-08-15
gnome shell from the repositories is very out of date. if u dont want to build from source, which i recommend altho its gnome shell is broken right now, u can use ricotz's ppa, which is more up to date.

1. i dont know how to do that. i just open my documents and then go to the trash from there.

2. i dont know how to do that either.

3. if you start gnome shell from the terminal, u can do Ctrl+C which will shut it down and go back to gnome 2. if u dont start it from the terminal u can do Alt+F2 and type **debugexit  **which will exit gnome shell and go back to gnome 2.

check this out for more interesting stuff
[http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

also here is the gnome shell test thread
[http://ubuntuforums.org/showthread.php?t=1476241](http://ubuntuforums.org/showthread.php?t=1476241)


```
$ sudo add-apt-repository ppa:ricotz/testing
$ sudo apt-get update
$ sudo apt-get install gnome-shell
```

---

### Post by Warthaug on 2010-08-16
Great - thanx for all that!

Bryan

EDIT: forgot to say, I'm fine with the out-of-date version in the repositories.  My goal was simply to give it a go, rather than any sort of hard-core testing, etc.  Gotta say, I like what I see so far, and I cannot wait for the final version

---

