---
title: "sshd and ssh - do I need them"
date: 2006-03-16
forum: Desktop Environments
---

### Post by frootstripe on 2006-03-16
Is there any reason I should have the sshd installed on a desktop I have no intention of logging into remotely? Also, is it the default behavior of Kubuntu to install ssh and the sshd?

I removed ssh but the sshd still runs in background. How do I remove it - couldn't do it with apt

thanks in advance

---

### Post by klahjn on 2006-03-16
[QUOTE=frootstripe]Is there any reason I should have the sshd installed on a desktop I have no intention of logging into remotely? Also, is it the default behavior of Kubuntu to install ssh and the sshd?

I removed ssh but the sshd still runs in background. How do I remove it - couldn't do it with apt

thanks in advance[/QUOTE]

do a search in synaptic for sshd.  you should be able to find the package that includes sshd and be able to remove it.  It will also graphically display what programs require sshd as a dependency and as such give you a more educated look on whether or not to remove it.

---

### Post by frootstripe on 2006-03-16
I was under the impression - from reading faqs and other posts - that synaptic breaks after one uses apt on the command line, so I guess synaptic isnt an option. Anyway, apt doesn't remove sshd, any suggestions as to how I should get it off my system? I'm pretty sure I don't need it. 

Also, reading up on the cleartext password problem, was that something specific to Ubuntu installer, or was that Kbu as well?

---

### Post by engla on 2006-03-16
[QUOTE=frootstripe]I was under the impression - from reading faqs and other posts - that synaptic breaks after one uses apt on the command line, so I guess synaptic isnt an option. Anyway, apt doesn't remove sshd, any suggestions as to how I should get it off my system? I'm pretty sure I don't need it. 

Also, reading up on the cleartext password problem, was that something specific to Ubuntu installer, or was that Kbu as well?[/QUOTE]
Oi, that sounds really strange that Synaptic should break. I've never experienced this, what have you heard?

Synaptic should work fine.
The package should be openssh-server and it's not installed by default

---

### Post by aysiu on 2006-03-16
[QUOTE=frootstripe]I was under the impression - from reading faqs and other posts - that synaptic breaks after one uses apt on the command line[/QUOTE] This is entirely untrue. Can you point to a link that says this, so I can try to contact the author and get her to change it?

Synaptic does not interfer with apt-get **unless** you're trying to apt-get while Synaptic is *open*. Only one at time.

---

### Post by frootstripe on 2006-03-16
I searched for posts, how-tos mentioning that apt breaks synaptic but couldn't find them, so I guess they've been removed or I was mistaken. Anyway, thanks for the replies, I was able to remove all ssh packages with synaptic (my first time using it!)

---

