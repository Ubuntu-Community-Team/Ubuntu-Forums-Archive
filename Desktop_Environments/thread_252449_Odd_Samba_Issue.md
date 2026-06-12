---
title: "Odd Samba Issue"
date: 2006-09-06
forum: Desktop Environments
---

### Post by skendale on 2006-09-06
Hey all,
I am trying to set up Samba and have an odd problem.
One partition is being recognized while the other is not.
Here is the end of my smb.conf:

[musica2]
path = /media/sda2/music
available = yes
browseable = yes
public = yes
writable = no

[musica]
path = /media/hdb1/READYTOGO
available = yes
browseable = yes
public = yes
writable = no

musica2 is visible, while musica gives me an error when trying to connect.
Any thoughts?
-skendale..

---

### Post by skendale on 2006-09-10
Any ideas for this?

---

### Post by barranco on 2006-09-10
I had a similar problem and had to change my directory group to match the one of the user accessing the share.

---

