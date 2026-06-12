---
title: "Reinstate kde 4.2 after 4.3 beta..."
date: 2009-05-21
forum: Desktop Environments
---

### Post by hoppy785 on 2009-05-21
i made the mistake of leaping before i looked, so they say.  i install kde 4.3 beta 1 on kubuntu 9.04 yesterday without first thinking how to go back.  so my question to the more experienced users is how do i get my kde 4.2 back?  i've read a few things but they were all dated and didnt relate directly to 4.3 beta 1.  i know sudo apt-get remove kubuntu-desktop will do nothing since its merely a meta package.  so please help me

---

### Post by Gen2ly on 2009-05-22
Huh, i think you're pretty much up the creek, hopppy.  KDE involves so many packages that trying to track all of them down would be a waste of your time.

---

### Post by jacksaff on 2009-05-22
Remove the repo with the beta from etc/apt/sources.list

apt-get update

then you could try apt-get remove kdelibs5
which nearly all of kde depends on.

You should then be able to apt-get install kubuntu-desktop and get the 4.2 packages.

I doubt this will fix it straight up but it should get rid of enough packages that you can remove the rest by reading the error messages and just keep going till k-desktop installs.

There must be a more elegant way but I don't know much about apt.

---

### Post by hoppy785 on 2009-05-22
removing kdelibs5 was kinda what i was thinking... hmm i must just stay with the beta.  it has some bugs but not many.  im afraid to start a process that would wreck my whole system that i couldnt fix.  if i backed up my home folder would it save all my programs and files or just files? also whats a good program to use for backing up a home folder.

---

### Post by hoppy785 on 2009-05-22
any other suggestions?

---

### Post by Gen2ly on 2009-05-22
Hmm, i think i'd just use tar:

```
tar -cvpzf --exclude /home/<user>/Home-Backup.tgz /home/<user>/Home-Backup.tgz /home/<user>
```

But probably a better way to do it is to just copy your Documents, Audio... and put it on a flash drive.  The above could be used to replace the wholehome folder but I'd be leary of that since kde 4 point 3 could have altered someconfig files and could cause bugs in the earlier version.

---

### Post by hoppy785 on 2009-05-23
bump... just seeing if anyone else has any suggestions other than remove kdelibs5

---

### Post by markuskalb on 2009-06-01
> **hoppy785 said:**
> bump... just seeing if anyone else has any suggestions other than remove kdelibs5

Hi 

you can use some documentation from "pure gnome" ([http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)) just use the remove part without the "apt-get install ubuntu-desktop" at the end of that very long line. Just don't do this from insider kde! Use a Console with Ctrl-Alt-F1 for example you get the first of them. 

After you changed your /etc/apt/sources.list by removing the kde 4.3 repo and using the long "apt-get remove" from above you can then do an "apt-get update" and an "apt-get install kubuntu-desktop" and it should install standard kde-4.2. 

That leaves us with the ".kde" dir inside your $HOME. I don't know if KDE 4.3 uses the same .kde dir as KDE 4.2 (installing kde 4.3 at the moment so i might now later). but if it does use the same dir and made changes to it you might need to get to your backups if you have some. If not it might get dicey. You could move the .kde to .kde-old and then switch back to kdm login with Ctrl-Alt-F7 and login and therefore create a new .kde dir. I then suggest that you log out again and again work from the console with maybe the "mc" program and look at the contents of ~/.kde/share/apps/ and ~/.kde-old/share/apps/. You should be able to rescue your data. I don't now if the apps dir is the only one that is used by programs so you might take a look at ~/.kde/share/config too. 


If you have questions just send me an PM. 

ciao markus

---

### Post by markuskalb on 2009-06-01
> **hoppy785 said:**
> removing kdelibs5 was kinda what i was thinking... hmm i must just stay with the beta.  it has some bugs but not many.  im afraid to start a process that would wreck my whole system that i couldnt fix.  if i backed up my home folder would it save all my programs and files or just files? also whats a good program to use for backing up a home folder.

Have a look at [http://idolinux.blogspot.com/2008/11/automate-rdiff-backup.html](http://idolinux.blogspot.com/2008/11/automate-rdiff-backup.html)  the skript there uses the very good program rdiff-backup and wraps some checks around it. This makes the use much more user friendly if you don't speak "rdiff-backup config language". 

ciao markus

---

