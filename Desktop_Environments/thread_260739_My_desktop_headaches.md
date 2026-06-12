---
title: "My desktop headaches"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Hiroshima on 2006-09-19
Ok, I thought that KDE was a bit slow, and when I discovered that some of my desktop icons weren't responding right, that I would try Xubuntu.  I installed " sudo aptitude xubuntu-desktop" as per the instructions here: [http://ubuntuforums.org/showthread.php?t=205002](http://ubuntuforums.org/showthread.php?t=205002)   xubuntu crashed almost instantly, and so I removed it with aptitude.  I then tried gnome, which seemed to be working, but now when I try to turn on the computer, gnome loads up, and the screen flashes, and does no more.

I don't want to just get rid of gnome, I like it.  

So, two things, how can I fix the gnome, when I don't really even know what is wrong?

And number two, I have both KDE and gnome set to automatic login.  Can I make it stop at the login screen to choose KDE while figguring out the Gnome question...  I thought about starting up in recovery mode... but I don't know how to get the login screen from there.  Or, on the other hand, how to turn off automatic login from terminal (recovery).

Any help would be great.

Hiroshima

---

### Post by someguyouknow on 2006-09-19
what default display manager are you using? you may have messed up there... thats what i did when i tried to install xubuntu.

---

### Post by Hiroshima on 2006-09-19
> **someguyouknow said:**
> what default display manager are you using? you may have messed up there... thats what i did when i tried to install xubuntu.

The default is set to KDE.

---

### Post by someguyouknow on 2006-09-19
make sure you have kdm as the desktop manager.  when you install ubuntu-desktop it ask whether you use kdm or gdm. so you might have to remove gdm and install kdm.

thats the only thing i can think of...
sorry if that doesnt help...

edit: in your link it says do sudo dpkg-reconfigure kdm

---

### Post by Hiroshima on 2006-09-19
> **someguyouknow said:**
> make sure you have kdm as the desktop manager.  when you install ubuntu-desktop it ask whether you use kdm or gdm. so you might have to remove gdm and install kdm.

thats the only thing i can think of...
sorry if that doesnt help...

Thanks, i'll give it a try tomorrow, I want to do it now, but can't be up all night.

Cheers, Hiroshima

---

### Post by Hiroshima on 2006-09-21
Sorry for taking so long to get back... thanks for all the advice.  I did the command "sudo aptitude remove ubuntu-desktop" and it seemed to have fixed the problem... even though it did not remove gnome... I'm confused as to why, but happy that (at least for now) I have a working Ubuntu and Kubuntu system.

Thank you for the help (and I should have noticed the reconfigure on my original link too) 

Thanks,

Hiroshima

---

