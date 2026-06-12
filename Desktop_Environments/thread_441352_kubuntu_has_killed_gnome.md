---
title: "kubuntu has killed gnome"
date: 2007-05-12
forum: Desktop Environments
---

### Post by glendavee on 2007-05-12
I've been running Ubuntu (7.04),  and decided to give Kubuntu a go. I installed it via apt-get, 
My problem is that I thought when I chose the gnome option at log-in, I would be back to my original setup, and if I chose KDE at login I would have KDE. What I got didn't matter which option I chose - its a mixture of KDE and gnome stuff, and my Wcid has disappeared. 
Decided to get rid of Kubuntu, and used apt-get remove Kubuntu-desktop, but there still seems to be a stack of Kstuff on my desktop. 
How do I get rid of all traces of Kubuntu?

---

### Post by taurus on 2007-05-12
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by glendavee on 2007-05-13
Thanks for prompt reply. Followed the instructions, but when the dialog box came up asking if I wanted to terminate the K stuff immediately, I chose "yes", system immediately shut down. On reboot, KDE desktop still there, so I tried to repeat the instructions, this time I get following :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

How do I do this?

---

### Post by rich.bradshaw on 2007-05-13
type

dpkg --configure -a

it will tell you need to be root, so

sudo dpkg --configure -a

---

### Post by glendavee on 2007-05-13
Thanks. Ran dpkg as suggested, then repeated the exercise, this time it worked. Kubuntu has gone. Problem solved.

---

