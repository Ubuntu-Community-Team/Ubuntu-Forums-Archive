---
title: "How do I get source code for my current packages?"
date: 2005-06-16
forum: Desktop Environments
---

### Post by raetsel on 2005-06-16
Hi,

I have a weird intermittent problem with Synaptic/apt.

I'd like to be able to get the source code for these packages so I can look through what is going on.

Sounds like a simple question but how do I get the source code? The main ubuntulinux.org website says there are patches and all the source code for all the packages but I can't find it?

Am I missing something? Can I set this up through apt-sources instead?

Thanks in advance.

Simon

---

### Post by Knome_fan on 2005-06-16
Hi,

apt-get source whateverpackage you want.

And make sure you also have the source repositories in your /etc/apt/sources.list.
They usually have the same address as the binary ones, they just start with deb-src, instead of deb.

Have fun poking around :-D

---

### Post by raetsel on 2005-06-17
Ah thanks Knome_fan that's the ticket. I thought it would be something simple. Though of course once you know it anything is simple.

Now what do all these #ifdef and for(i=0,i<5,i++) mean?  :grin: 

Simon

---

