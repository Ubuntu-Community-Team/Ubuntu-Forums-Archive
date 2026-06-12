---
title: "Root password lost after update"
date: 2009-02-16
forum: General Help
---

### Post by chrisbloe on 2009-02-16
I have just updated PAM (about 20 min ago) from sudo apt-get upgrade and selected to 'override' at the prompt.

Now I can't use my sudo password... has it been reset? What is it??

Many thanks,

Kris

---

### Post by gettinoriginal on 2009-02-16
Here ya go, try this:  :p
[http://www.ubuntugeek.com/howtorecover-your-username-and-passwordfix-grub-21-error-in-ubuntu.html](http://www.ubuntugeek.com/howtorecover-your-username-and-passwordfix-grub-21-error-in-ubuntu.html)

---

### Post by chrisbloe on 2009-02-17
Many thanks, but I've found out that the module I updated was libpam-ck-connector. I believe this links the password entry to where it's meant to go.

If I understand correctly, the password is fine, but the connecting bit is damaged.

I still need to find a way of solving this... I don't really want to re-install just because of this.

---

### Post by gettinoriginal on 2009-02-17
Have you tried going to Synaptic and reinstalling libpam-ck-connector ?

---

### Post by chrisbloe on 2009-02-18
That would be nice... if only my password would let me open Synaptic!

It doesn't matter anymore, I formatted and installed Jaunty on the new ext4.

Thanks anyway.

---

