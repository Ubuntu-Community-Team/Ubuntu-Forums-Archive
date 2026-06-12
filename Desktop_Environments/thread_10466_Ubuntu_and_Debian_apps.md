---
title: "Ubuntu and Debian apps"
date: 2005-01-08
forum: Desktop Environments
---

### Post by Drevil on 2005-01-08
Seeing as Ubuntu is based on Debian, would it work doing apt-get to a Debian repository.

A lot of people here at work run Debian and we have a local server for all the Debian packages.

I have not installed Ubuntu yet, just asking if Debian packages/apps would work on Ubuntu.

Thx

---

### Post by machiner on 2005-01-08
That's what I run -- but it took a little work - nothing hard or challenging - just fix the error messages you will see. There are a couple proggys to remove, you'll see which ones with the errors you will get, like 5 proggys, and gnome-panel is one...put it back when you're done.

I install Ubuntu - update and upgrade it using Ubuntu's repositories (NOT universe or multiverse) then I add a debian repo:

[http://ftp.debian.org/debian/](http://ftp.debian.org/debian/)
testing
main contrib

pic --->[www.madcarters.com/repo.png](www.madcarters.com/repo.png)

THen I update again. Usually about 500 packages get updated...I reboot and whamo - I have the debian menu, login manager and debian proggys...ubuntu kernel.
As you can see from the pic - I don't use ubuntu repos anymore...and if anything should happen I have backup images of each step of the way...

good luck

---

### Post by fng on 2005-01-08
[QUOTE=Drevil]Seeing as Ubuntu is based on Debian, would it work doing apt-get to a Debian repository.[/QUOTE]

Yes, but its not recommended.  Its better to stay with the ubuntu repositories.

---

### Post by machiner on 2005-01-08
Linux is for the daring - the inquisitive - the tinkerer. Don't scare this idea off - I might not do what I do on a production box (even though my box does make me $$) but I have seen zero (that's "0") errors.

It's a glorious thing.

Oh -- Linux is also for the frustrated windows user - but your hope is misplaced. Learn windows, or go back to pencil and paper. You'll be happier.

---

