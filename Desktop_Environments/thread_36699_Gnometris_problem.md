---
title: "Gnometris problem"
date: 2005-05-24
forum: Desktop Environments
---

### Post by lhtown on 2005-05-24
OK, so I like to play gnometris sometimes.

It works fine, but I have a problem. Recently, I was playing on my desktop while I had Gnometris open and I dragged and dropped a photo that I had on my desktop into the background of the play area in gnometris. 

To my surpise, it displays the image in the background of Gnometris. Now, I can't get it out. I even tried reinstalling the program, deleting the file and looking for settings that might offer an option to change it. All has been to no avail. The picture is still there as a background.

Can anyone offer any suggestions as to how I can get that photo out of the background?

---

### Post by basse1989 on 2005-05-24
Do this in a new terminal
```
rm .gnome2/gnometris.d/background.bin
```
This will not effect anything except getting rid of the background.
Happy playing  :)

---

### Post by lhtown on 2005-05-24
Thanks, I now have a beautiful, black background- the image is gone!

---

