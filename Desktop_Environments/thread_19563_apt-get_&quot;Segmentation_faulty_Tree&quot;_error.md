---
title: "apt-get &quot;Segmentation faulty Tree&quot; error"
date: 2005-03-12
forum: Desktop Environments
---

### Post by totalshredder on 2005-03-12
hey everybody, I have a problem. I can no longer use apt-get or synaptic. When I do I get the following:

Reading Package Lists... Done
Segmentation faulty Tree... 50%

It happens whenever I do anything. Here's how I think it happened; I was upgrading to horay (I'm using warty now) and when I did a "dist-upgrade" it got about half way or so and quit. Now, I get my error.

What can I do?

Thanks!

Luke

---

### Post by totalshredder on 2005-03-30
Hey Ya'll,

   Just in case anyone gets this same problem and is searching around, here's what you do:

```
sudo rm /var/cache/apt/*.bin
``` 

   I have experienced no problems/side effects from this, an it works like a charm! Thanks to [this](http://lists.debian.org/debian-user/2000/03/msg00861.html) fellow over at the debian forums for the answer :)


Luke

---

### Post by dream_coder on 2008-05-17
thanks ever so much for this i asked in the chat room but i was told i had to do a fresh install pfft thanks again worked like a charm

---

