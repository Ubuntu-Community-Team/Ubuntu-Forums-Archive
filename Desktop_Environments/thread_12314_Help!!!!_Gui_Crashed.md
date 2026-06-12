---
title: "Help!!!! Gui Crashed"
date: 2005-01-23
forum: Desktop Environments
---

### Post by new2linux on 2005-01-23
Hi,

   I just recently installed ubuntu.  I am new to Linux, and I was trying to set up some themes I found online.  Their installers said that I needed gtk-+2.0.  I went into the debian website and found a package labeled libgtk2.0 or something like that.  I guessed that it was the right package.  I tried 2 run it, and now, when i boot my
compy it says

> "There already appears to be an x server running on display:0  Should
I try another diplay number?  If you answer no, I will attempt to
start the server no :1 again"

I have tried hitting enter several times, to no avail.

I somehow got into the command line and it works fine.  So maybe there isn't a major problem with the O.S.

ne ideas on what I did and how I can fix me gui?



EHD

---

### Post by DJ_Max on 2005-01-23
From my understanding, if you had a GUI started up, then you already had GTK+. Either way, you should have done.

```
sudo apt-get install libgtk2
``` 

There is no problem with the OS, just the x-server and gnome config.

When you say you " tried 2 run it", what do you mean? You installed the deb package?

---

### Post by new2linux on 2005-01-23
Thanx 4 responding

I installed the deb file

as in dpkg -i (package name)

How do I get the gui back up and running?

EHD

---

### Post by shmonkey on 2005-01-23
Sounds like you have installed a standard debian package file. I don't know why you did it this way. Youi should really use ubuntu packages from the repostitory as suggested by DJ_Max.

I would issue these commands from the command line

```
# sudo killall gdm
# sudo dpkg -r <path-to -your-deb-file/your-deb-file>
# sudo apt-get install libgtk2.0-0
# sudo gdm
```

---

### Post by new2linux on 2005-01-23
Thanks Everyone!!!!!!!!!!!!!!!!

Gui Is Back Up And Running!!!!!!!!!

Ehd

---

