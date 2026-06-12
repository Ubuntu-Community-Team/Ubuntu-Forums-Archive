---
title: "Installing Beryl with an ATI card"
date: 2007-06-21
forum: Desktop Environments
---

### Post by Tekee on 2007-06-21
Someone recommended I use this site to help me out:

[http://ubuntu1501.blogspot.com/2007/04/beryl-in-feisty-with-xgl.html](http://ubuntu1501.blogspot.com/2007/04/beryl-in-feisty-with-xgl.html)

It went along fine until I had to do this:

```
In a terminal type:
sudo gedit /usr/local/bin/startxgl.sh

and this to the file:
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
save and close file

Then make the xgl script executable by entering this into a terminal:
sudo chmod a+x /usr/local/bin/startxgl.sh
```

When I tried to enter that text into the file they gave me, it gave me an error that there is no such file. 
Any ideas?

EDIT - I looked through the folder and I do have a startx.sh file....would that possibly be the same thing?

---

### Post by swisscow on 2007-06-21
If the file doesn't exist, the command will create it. If it does exist, the command will open it.

All I can suggest is that you check that you have put the command in correctly. However, another thing to consider is if you are using KUBUNTU, this file (I think) goes somewhere else, but I can't remember where!

---

### Post by freshmeatz on 2007-06-21
When i tried this method a few months ago it didn't cut it for me either , I have a rv350 ATI or better known as the 9550 ..


:o

---

### Post by freshmeatz on 2007-06-21
> **Tekee said:**
> Someone recommended I use this site to help me out:
[
EDIT - I looked through the folder and I do have a startx.sh file....would that possibly be the same thing?

post the file startx.sh to see 

In a terminal type:
sudo gedit /usr/local/bin/startx.sh

---

### Post by Tekee on 2007-06-21
Nope, not using KUBUNTU =/

And I tried it for the other start.sh file as well...gave me the same error!

---

### Post by freshmeatz on 2007-06-21
> **Tekee said:**
> Nope, not using KUBUNTU =/

And I tried it for the other start.sh file as well...gave me the same error!

you mean startx.sh?

---

