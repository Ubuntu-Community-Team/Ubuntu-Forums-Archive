---
title: "Can't find my usual Debian apps."
date: 2005-05-19
forum: Desktop Environments
---

### Post by chris_andrew on 2005-05-19
Hi, all.

I am currently using Debian Sarge on my main box.  On a spare, I have installed Hoary.  

I like what I see, but am concerned that some of my favourite apps aren't available, such as XFCE (and its various add-ons), fvwm and gtk-gnutella.

I uncommented the universe lines in /etc/apt/sources.list, did an apt-get update, apt-get upgrade, but can't find these apps.

Anybody know whether they are available under Ubuntu?

Thanks,

Chris.

---

### Post by infinito on 2005-05-19
[QUOTE=chris_andrew]Hi, all.

I am currently using Debian Sarge on my main box.  On a spare, I have installed Hoary.  

I like what I see, but am concerned that some of my favourite apps aren't available, such as XFCE (and its various add-ons), fvwm and gtk-gnutella.

I uncommented the universe lines in /etc/apt/sources.list, did an apt-get update, apt-get upgrade, but can't find these apps.

Anybody know whether they are available under Ubuntu?

Thanks,

Chris.[/QUOTE]
 You have to enable universe and multiverse on /etc/apt/sources.list
Just add those words to the main sources.list lines

---

### Post by chris_andrew on 2005-05-19
Infinito,

Success.  When I added Multiverse before, I commented-out universe.  I now have both, and over 16000 apps available to me, just like Sarge.

Cheers,

Chris.

---

