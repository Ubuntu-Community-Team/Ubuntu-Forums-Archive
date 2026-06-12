---
title: "My wallpaper is stuck!"
date: 2008-04-14
forum: Desktop Environments
---

### Post by InGunsWeTrust on 2008-04-14
This problem has a bit of a back story. If you are interested in the story -- At my school if somebody walks away from their computer without locking it we made this fun game of setting their wallpaper to something funny. Me being the enterprising Linux buff that I am decided to make that impossible. I used gconf-editor (screenshot below) to set the picture_filename key as mandatory. This certainly did prevent anybody from changing my background, however I noticed next time I booted my wallpaper was set to the default wallpaper and I could not change it either!


For those not interested in the story (or those done with the story):

The short story is I can't change my wallpaper because I set it as mandatory. I tried to open gconf-editor as root to change my wallpaper back, but it still wouldn't let me change it back. I tried to "unset" the key to see if I could completely delete it and remake it, but it never went away. I even tried opening firefox as root and right clicking an image to set as background.

Attached is the screenshot mentioned above and my .gconf desktop configuration file

---

### Post by russo.mic on 2008-04-14
just to make sure, your running gconf-editor with sudo, right?  and to fully understand, you can change it if you point gconf-editor to a different file, right?

Russo

---

### Post by InGunsWeTrust on 2008-04-15
Yes, that is my issue. With sudo, I cannot change the setting still.

---

### Post by rainwalker on 2008-04-15
I can't help you with your problem, but I learned that it's good practice to use "gksudo" instead of "sudo" when you're launching an application that uses a GUI instead of using a command.

---

