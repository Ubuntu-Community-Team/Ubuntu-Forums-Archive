---
title: "[SOLVED] Thinking about installing Fedora"
date: 2008-12-30
forum: Fedora/RedHat and derivatives
---

### Post by theozzlives on 2008-12-30
I'm thinking about putting Fedora 10 (looks promising) on my desktop, but don't know how compatible it is with my Ubuntu knowledge. Like what's the equivlent of apt-get and sudo and stuff. Will my shared printer still work across the network, etc.

---

### Post by Vince4Amy on 2008-12-30
You can Install/Enable sudo on Fedora, though it's recommended that you simply use the root account by typing su first and then doing administrative tasks.

To install software it's yum install softwarename

---

### Post by theozzlives on 2008-12-30
what about samba?


I installed Fedora in a VirtualBox, installed Samba and can't access my shares.

---

### Post by igknighted on 2008-12-31
> **theozzlives said:**
> what about samba?


I installed Fedora in a VirtualBox, installed Samba and can't access my shares.

You probably need to unblock the firewall ports?  It worked right away for me...

---

