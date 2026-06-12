---
title: "I want my folder theme back"
date: 2010-08-03
forum: Desktop Environments
---

### Post by Karim_ on 2010-08-03
I don't know how this happened, it just did, I was messing around and suddenly I put the  download folder in the music folder and when I got it back out to the home folder it turned to a normal plain folder just like in windows vista.

How do I change it back. Just tell me what to do!
[[COLOR=Blue]Picture[/COLOR]]("http://public.blu.livefilestore.com/y1pyvFw6UIwr6FCPQrEVoJTQ5VPK0MvH9flUQWtGp0S0IwaI6edzRlxc6RKKzD2J4bUN6WCE-sTvgrEWboiDXiANw/Screenshot.png?psid=1")

---

### Post by hansdown on 2010-08-03
Hi Karim_.

Open your downloads.

Click edit> pictures and emblems> emblems.

Scroll down the the downloads emblem, and drag and drop it to the downloads.

You should have the folder back to the same.

---

### Post by Karim_ on 2010-08-03
This is not the same as the old. As you can see in your home folder it's a more nicer image of a arrow pointing down.

---

### Post by mcduck on 2010-08-03
You need to edit the ~/.config/user-dirs.dirs -file and make sure that the "XDG_DOWNLOAD_DIR" is set to "$HOME/Downloads".

This entry was most likely removed/changed when you moved the Downloads directory away from your home.

You might have to log out and back again after fixing the file to see the changes.

---

### Post by Karim_ on 2010-08-03
OK. It's fixed now. 

Thanks.

---

