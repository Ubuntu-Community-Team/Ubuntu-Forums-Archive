---
title: "Ubuntu freezes when I rm or empty trash"
date: 2009-05-28
forum: General Help
---

### Post by googlegot on 2009-05-28
Ubuntu keeps freezing whenever I rm large files or empty the trash.

I have not been able to find the error when I look through any logs.

Does anyone know why this happens?

---

### Post by JohnB-nbr on 2009-05-28
Is your filesystem ext4?

---

### Post by googlegot on 2009-05-28
yessir

---

### Post by JohnB-nbr on 2009-05-28
I asked that question because I've read a couple of bug reports on the same matter.

---

### Post by mkvnmtr on 2009-05-28
I sometimes have the same problem on my b9.04 that has ext4 for a format. I reinstalled on my other unit and formated ext3 and no longer have the problem. It seems to be related to ext4 and does not seem to affect everyone.For some people it seems to be very bad and has led to losing data. You might need to reinstall and change your format. I believe when I have time I will do that on my system that still has ext4.

---

### Post by googlegot on 2009-05-28
I fixed my issue as well as a few other issues I was having with system performance with a simple kernel update from the ubuntu kernel website.

Heres a guide:
[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)

---

### Post by JohnB-nbr on 2009-05-28
Thank you for the update googlegot!

---

### Post by googlegot on 2009-05-28
> **JohnB-nbr said:**
> Thank you for the update googlegot!

No problem, this issue has pissed me off since I started playing with virtual machines, I hope it helps a couple people

---

### Post by cdysthe on 2009-07-27
> **googlegot said:**
> No problem, this issue has pissed me off since I started playing with virtual machines, I hope it helps a couple people

I am having the empty trash problem on my laptop. However, I see such a speed gain in ext4 over ext3 that I would like to keep the filesystem and empty trash in another way for now. What I wonder about is if this is caused by ext4's ability to delete a lot of files at once, or if it's Gnome's trash can implementation not being compatible with ext4 at this point. Does anyone know?

---

### Post by donpaolo on 2012-07-13
I have this problem with ubuntu precise. I hadn't it with oneiric.

Filesystem ext4.

---

### Post by overdrank on 2012-07-13
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

