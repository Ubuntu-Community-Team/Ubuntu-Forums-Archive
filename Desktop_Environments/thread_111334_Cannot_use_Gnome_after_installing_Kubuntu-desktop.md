---
title: "Cannot use Gnome after installing Kubuntu-desktop"
date: 2006-01-02
forum: Desktop Environments
---

### Post by Deneb Algedi on 2006-01-02
I just installed kubuntu-desktop on my Ubuntu(Gnome system) because I wanted to know which one I like best. I was told you could install both on 1 computer without problems with "kubuntu-desktop".
But now I cannot start Gnome anymore. I just get a lot of GomeWarning sounds and a brown screen. Is there any way to solve this problem?

---

### Post by Jammy_Stuff on 2006-01-02
You could try reinstalling ubuntu-desktop

---

### Post by The Hedgehog on 2006-01-02
I Already did, but it didn't help.

---

### Post by Deemo on 2006-01-02
in the login screen, press the Session button. Select GNOME and it should switch. I dont know if you have already tried this or not, but it needs to be asked :P

---

### Post by jrib on 2006-01-02
This happened to me.  It made me very frustrated and I immediately removed kubuntu.  Like you, the damage had been done.  Hopefully, what I did will also work for you.  I created a new user and everything worked fine.  I just copied over my documents and deleted the old user from the system.

---

### Post by aysiu on 2006-01-03
Try [this](http://www.ubuntuforums.org/showthread.php?t=96048).

---

### Post by jrib on 2006-01-03
Oh, I thought you had removed kubuntu already.  I just did 'sudo apt-get remove libqt3-mt'.  All of the kubuntu stuff should depend on that library and go along with it if you used something that keeps track of dependencies like apt-get or synaptic.  I'm sure aysiu's method would work as well.

I seem to recall that the nature of the problem was a library for using gtk in the qt environment of kde.  Removing that library allowed me to login to gnome but my settings got messed up from kde.  Unfortunately, I don't recall the name of the package. Maybe someone knows what I'm talking about.

[edit] I searched some logs and found that the exact package I had to remove was: gtk2-engines-gtk-qt

---

### Post by fangorious on 2006-01-04
I just deleted the .gtktrc*files in my home directory and that fixed it.

---

