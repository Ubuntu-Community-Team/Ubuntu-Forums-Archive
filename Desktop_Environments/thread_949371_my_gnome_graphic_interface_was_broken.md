---
title: "my gnome graphic interface was broken"
date: 2008-10-16
forum: Desktop Environments
---

### Post by Rayvantuhesa on 2008-10-16
:)hi
I like my gnome very much, but now I can't enjoy my gnome because it was broken. when I actived the compiz fusion, it would log out automatically. so I had to change my graphic interface with the others, like kde. Someone, please help me.. I dont know much about this coz I am a newbie.

---

### Post by larseko on 2008-10-16
Have you tried resetting your GNOME configuration by deleting ~/.gnome~ and /.gnome2? Be careful if you have email settings or other special setup that you can't restore easily.

To delete, open a terminal in KDE (not sure where you find it there), and type (be very careful, rm -rf deletes all in its way (ie paths) without asking for confirmation) :

rm -rf ~/.gnome ~/.gnome2 

Maybe also rm -rf ~/.gconf

Hope that helps.

---

### Post by Rayvantuhesa on 2008-10-19
thank a lot larseko. Now, My GNOME is more stable.
but, it is going unstable and always log out automatically when I try to activate the advance desktop effect setting. What should I do?

---

### Post by Dave_Connor on 2008-10-19
Is there a way you could post the output of running compiz in terminal ? compiz --replace I think is the command.

---

