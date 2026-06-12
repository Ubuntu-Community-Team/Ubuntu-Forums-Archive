---
title: "[SOLVED] Password screwed up?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Thorndeux on 2006-08-06
I was away for a couple of weeks and there were lots of updates today. Now I have the following problem:

My root password is not accepted (tried running synaptic) - and: no typo.

Do people have the same problem?
What can I do about it?

Thanks
Thorn


Edit: It says a reboot is required. I didn't do that until now, because I fear it won't allow me to log back in...
Edit 2: I did reboot now. Could log in fine. Synaptic still doesn't accept my password.

---

### Post by Thorndeux on 2006-08-06
Bump

---

### Post by liquideath on 2006-08-06
Exact same problem here, but I have had other problems as well. I posted about it in [this thread]("http://www.ubuntuforums.org/showthread.php?t=230476"), but haven't got it figured out yet. It seems "gksudo" was replaced with "gksu," which doesn't work.

---

### Post by Thorndeux on 2006-08-06
That's a start. I guess I'll come back to it after i finished my thesis.

---

### Post by Thorndeux on 2006-08-07
Resolved!

Thanks to liquideath's hint I updated via the terminal:
```
sudo aptitude update
sudo aptitude dist-upgrade
```
Now it works. So, it seems that Synaptic didn't work because it uses an updated version of gksudo called gksu which, in turn, was not correctly installed. For infos on sudo and gksudo (or gksu) see [this page]("http://www.psychocats.net/ubuntu/graphicalsudo.php"), which helped me to understand the whole sudo/gksudo business. As aptitude (or apt-get) doesn't use gksudo but sudo, it still worked to update via aptitude.

---

