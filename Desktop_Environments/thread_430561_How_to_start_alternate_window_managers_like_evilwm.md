---
title: "How to start alternate window managers like evilwm, icewm?"
date: 2007-05-02
forum: Desktop Environments
---

### Post by penman242 on 2007-05-02
Hi, I'm running ubuntu 704.  I have installed evilwm, twm, maybe a couple of others, but they don't show up in my session choices (in I think what is called the gdm).  How do I get them to show up there, or otherwise choose them for my session?   Thanks.

---

### Post by penman242 on 2007-06-10
You can install fluxbox and then change to twm, from the fluxbox menu.  WindowManagers -> Twm

---

### Post by fakie_flip on 2007-06-10
echo "exec twm" > ~/.xinitrc

---

### Post by fakie_flip on 2007-06-10
See this post to get it added into your sesssions menu from gdm.

[http://ubuntuforums.org/showthread.php?t=187443&highlight=twm+gdm+session](http://ubuntuforums.org/showthread.php?t=187443&highlight=twm+gdm+session)

---

### Post by fakie_flip on 2007-06-10
Double post, sorry.

---

### Post by penman242 on 2007-06-30
Thank you for your posts, fakie_flip.  The advice given in the thread you referred to worked like a charm!

---

