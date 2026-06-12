---
title: "Logout command works for one user, but not another"
date: 2009-10-08
forum: Desktop Environments
---

### Post by ST3ALTHPSYCH0 on 2009-10-08
Alright, I went through the process of making Ubuntu 9.04 look like OSx (turned out pretty good, too), and I added a launcher to AWN with the command "gnome-save-session--logout-dialog" so that I could switch users. It works flawlessly in my first account, but doesn't do anything in my wife's account. Her account currently has admin rights so that I can set hers up like mine, but I will be rescinding that after setup so that she doesn't have the ability to gank up the computer. 
I'd really appreciate any help, and yes, I am a complete n00b.... this is only my 4th day ever using Ubuntu.

***********EDIT*****************
I created a test account just to see if this was isolated to her account. this one actually gave me an error dialog that reads "Failed to execute child process "gnome-session-save--logout-dialog" (no such file or directory)

---

### Post by ST3ALTHPSYCH0 on 2009-10-09
Turns out that I forgot a space in my command line. It should read "gnome-session-save --logout-dialog". Wow, I feel like a 'tard. Dunno how, or if I even can, but can a mod please mark this one "solved"? Thanks a bunch

---

### Post by Albert Net on 2010-01-07
In spite of that, the right command should be ```
gnome-session-save --logout-dialog
```

---

