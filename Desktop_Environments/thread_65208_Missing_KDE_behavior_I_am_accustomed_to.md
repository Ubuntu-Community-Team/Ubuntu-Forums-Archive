---
title: "Missing KDE behavior I am accustomed to"
date: 2005-09-13
forum: Desktop Environments
---

### Post by pwolfe on 2005-09-13
I am a long time Mandrake user that has jumped ships to Kubuntu.  Never been happier with an OS before.  There is however one thing I sorely miss.  In Mandrake and every other distro I have used; highlighting a selection of text would act as copy, and middle mouse would paste the selection.  Kubuntu doesn't seem to do this.  Embarrassingly enough, that feature is probably my single favorite thing about linux =).  How can I enable this functionality in kubuntu?  Its not klipper, as it should work in other WMs and DEs but does not. 

Thanks in advance!

---

### Post by djib on 2005-09-13
[QUOTE=pwolfe]I am a long time Mandrake user that has jumped ships to Kubuntu.  Never been happier with an OS before.  There is however one thing I sorely miss.  In Mandrake and every other distro I have used; highlighting a selection of text would act as copy, and middle mouse would paste the selection.  Kubuntu doesn't seem to do this.  Embarrassingly enough, that feature is probably my single favorite thing about linux =).  How can I enable this functionality in kubuntu?  Its not klipper, as it should work in other WMs and DEs but does not. 

Thanks in advance![/QUOTE]
 Hello,

Does the middle button work ?
I mean when you are in Konqueror and click with the middle button on a link, does it open the link (in a new thread) or not ?

In case not, this could be the problem. My Kubuntu pastes fine.

---

### Post by Curlydave on 2005-09-13
I don't know about highlighting or KDE, but middle-click copys and pastes in Gnome Ubuntu.

---

### Post by Dolphin on 2005-09-13
From what I've seen so far, the middle mouse click does not workby default in kubuntu.  I had to edit my xorg.conf file to enable it.

---

### Post by djib on 2005-09-13
pwolfe, what you can do is : instead of editing your xorg.conf, type in ```
sudo dpkg-reconfigure xserver-xfree
``` and there you will get to choose if you want to have this third button working.

---

### Post by pwolfe on 2005-09-13
thanks for the replies everyone.  I'm hesitant to reconfigure X through dpkg, because the middle mouse button currently works.  That is to say that middle mouse clicking a link opens it in a new tab (firefox).  Its just the copy/paste that wont work.  It also scrolls.

---

### Post by cwaldbieser on 2005-09-13
[QUOTE=pwolfe]thanks for the replies everyone.  I'm hesitant to reconfigure X through dpkg, because the middle mouse button currently works.  That is to say that middle mouse clicking a link opens it in a new tab (firefox).  Its just the copy/paste that wont work.  It also scrolls.[/QUOTE]
Is klipper running in Kubuntu?  When you highlight text, can you click on the klipper applet and see the highlighted text in it?

---

### Post by pwolfe on 2005-09-14
klipper is not running, but the functionality should be there without it.  It doesnt work right in other wm's that dont rely on klipper either.  And the first thing I always do when loading into kde for the first time is disable klipper; In other distro's it would work without klipper.

---

### Post by pwolfe on 2005-09-14
Just as a test I started klipper back up.  That didnt do it either =(

---

### Post by djib on 2005-09-14
[QUOTE=pwolfe]Just as a test I started klipper back up.  That didnt do it either =([/QUOTE]
 Just a simple question, why don't you like klipper ?

---

### Post by pwolfe on 2005-09-14
I dont like the annoying pop-ups it does (I know you can disable that), and I've never really needed a history of the things I copied to clipboard.  Just one more thing running I dont need, so I dont bother with it.

I think it did something that really razzed me a LONG time ago too, and I disabled it anger.  Your question brings back memories of that moment, but not what it did to cause it =)

---

### Post by djib on 2005-09-14
[QUOTE=pwolfe]I dont like the annoying pop-ups it does (I know you can disable that), and I've never really needed a history of the things I copied to clipboard.  Just one more thing running I dont need, so I dont bother with it.

I think it did something that really razzed me a LONG time ago too, and I disabled it anger.  Your question brings back memories of that moment, but not what it did to cause it =)[/QUOTE]
 ok ;)
I never got popups myself and I REALLY like the history !

---

### Post by pwolfe on 2005-09-15
bump, this is driving me mad!

---

