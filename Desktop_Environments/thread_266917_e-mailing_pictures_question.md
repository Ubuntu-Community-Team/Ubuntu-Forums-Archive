---
title: "e-mailing pictures question"
date: 2006-09-27
forum: Desktop Environments
---

### Post by norcalnewb on 2006-09-27
My wife is a big fan of e-mailing pictures.  She recently mentioned to me that Windows (no longer on our computer) had an option that when you right clicked on a picture file would allow to downsize the picture for e-mail.  She would like the same capability when using Gnome and Evolution.  Is there a way to set this up?

Thanks,

Jim

---

### Post by kidders on 2006-09-27
You could create a bash script to pass it through Imagemagick and into your mail program, perhaps ... assuming Evolution's command line parameters support references to attachments.

Kmail would certainly cooperate (via dcop).

---

### Post by norcalnewb on 2006-09-27
That is what I was thinking, but I am not sure how to pass the pictures through to evolution.

---

### Post by kidders on 2006-09-27
I don't have it installed, so I can't check its command line options myself :-( I'm willing to bet someone has already thought of this though, and written a Nautilus extension for it.

---

### Post by asplode on 2006-09-28
There is a way to do it with a nautilus script... I can't seem to find it at the moment, so I'm going to upload the script...

extract it and place this in your ~/.gnome2/nautilus-scripts/ directory.

I love it, I use it to create batch thumbnails all the time.  Works like a charm, even better than anything I've found for windows.

---

### Post by norcalnewb on 2006-09-28
Thanks for the script.  That makes it easy to resize the image.  Should be enough for now.

---

