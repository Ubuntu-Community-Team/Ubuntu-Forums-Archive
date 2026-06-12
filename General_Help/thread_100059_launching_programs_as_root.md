---
title: "launching programs as root"
date: 2005-12-06
forum: General Help
---

### Post by tommmm on 2005-12-06
How can I make programs (in this case amarok and k3b) always run as root without asking me for a password?  Now I launch them with gksudo which of course prompts me for the password.  I have tried modifing my sudoers.tmp file with the line:

thomas ALL= NOPASSWD: /usr/sbin/firestarter, /usr/bin/amarok, /usr/bin/k3b 

at the end.  Firestarter works fine and never prompts me for a password, but the other two do.  Am I doing something very obviously wrong?  I have also tried giving each program a line of it's own in the sudoers with the same result.

---

### Post by aysiu on 2005-12-06
I find it odd that you even feel the need to run K3B or AmaroK as root. Can you indulge my curiosity and say why? I understand programs like Synaptic Package Manager or the Login Screen Setup, but you don't need to run K3B as root.

In any case, a password builds security. If you don't want security, just set up a root account and log in as root, and you can run whatever you want as root... I just don't see why you'd want to do that.

---

### Post by tommmm on 2005-12-07
Because both these programs simply refuse to work or crash on boot if i do it any other way.

---

