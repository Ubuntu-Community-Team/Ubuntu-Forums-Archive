---
title: "Add/Remove Programs has disappeared"
date: 2006-06-11
forum: Desktop Environments
---

### Post by gpierce on 2006-06-11
I just noticed this morning that the Add/Remove program, that used to be at the bottom of my Gnome Applications menu has vanished. I checked whether it was visible in the a la carte editor and it was not. Any thoughts on how to recover that functionality?
Greg

---

### Post by Ubuntuud on 2006-06-11
gnome-app-install, in a terminal. You can also make a new entry in the menu and assign the command to it.

---

### Post by gpierce on 2006-06-11
Actually I issued the "apt-get install ubuntu-desktop" command in a terminal and that fixed it. It's strange, however. I don't know what I did to cause it to disappear in the first place.


Thank you for the reply. I am continually amazed by the generosity and kindliness of this community.It is a welcome escape from most reality outside Linux.

Greg

---

### Post by Ubuntuud on 2006-06-11
I get amazed by it myself, I have many more questions than I can answer, I help people with what I know, but that's very limited, but it grows by the questions I ask and (ofcourse) because I toy with my machine. In the beginning of the year I barely heared about linux, but the community helped me out with (almost) all of my questions. But it's not "linux", I tried Gentoo once, but if you ask a question there for the second time, everybody starts complain (curse).

---

### Post by vixinu on 2008-04-11
In case anyone is still reading this thread, I have an answer to WHY it happened. You probably removed ubuntu-desktop by trying to sync time and date to the internet, and ubuntu-desktop includes programs such as add-remove, evolution, and others.

---

