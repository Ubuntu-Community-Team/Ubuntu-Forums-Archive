---
title: "I don't have permission to move a file?"
date: 2009-02-18
forum: General Help
---

### Post by Rumbl3 on 2009-02-18
Well i'm sure this question has been asked on here a hundred times.

Well i downloaded a new screensaver from gnome-looks.org and when i try to move the files into /usr/shared/gnome-screensavers it denies me and says i don't have permission. 

Just curious if anyone can tell me what i need to do to get it to allow me move the files there?

thx

---

### Post by x33a on 2009-02-18
move it with sudo.

sudo mv filename /usr/shared/gnome-screensavers

---

### Post by octesian on 2009-02-18
In general, anything outside your /home/username/ folder will require root privileges to access.  sudo temporarily gives you root privileges (after prompting you for your password).

---

### Post by xlxx on 2009-02-18
you might not be an administrater.
[http://dragcave.net/user/zatog]("http://dragcave.net/user/zatog")

---

