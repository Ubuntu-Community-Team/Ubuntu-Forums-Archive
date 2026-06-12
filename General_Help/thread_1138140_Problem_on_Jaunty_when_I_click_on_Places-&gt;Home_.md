---
title: "Problem on Jaunty: when I click on Places-&gt;Home movie player starts instead nautilus"
date: 2009-04-26
forum: General Help
---

### Post by vevo on 2009-04-26
Hello,

I just installed Jaunty on HP Compaq nx6125. When I click on Places-->Home (or Desktop, Documents..) movie player attempts to open it (instead of nautilus.)

If I click on a folder on the desktop nautilus opens it, as it has to be.

How can I teach jaunty that what is in "Places" is not a movie file but a folder?

Thank you
vevo

---

### Post by vevo on 2009-04-29
Solved.. I forgot to say I was using the same /home I had in ubuntu8.04. I deleted the folder .local in my home and now everything works fine.

vevo

ps. How do I tag my post as [Solved]?

---

### Post by dimitrisk on 2010-12-20
Just open a terminal and run the following command:
```
sudo rm -fr ~/.local
```

---

### Post by garvinrick4 on 2010-12-20
If you right click on any directory and choose open with and select file browser and check the box to open all like this with this it will do so. Have seen this quite often where a directory all starts opening in a media player. User accidentally tells it to do so. Done it myself is how I know.

---

