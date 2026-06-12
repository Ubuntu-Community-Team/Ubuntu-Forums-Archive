---
title: "Ubuntu Won't boot properly as secondary OS"
date: 2009-06-17
forum: General Help
---

### Post by ryan.megatron on 2009-06-17
[COLOR="SeaGreen"]I used the wubi installer to install Ubuntu 8.10 as a dual boot OS on my Windows XP laptop. It seems to work fine at first. When I turn on the computer, it asks me to choose Windows XP or Ubuntu. I choose Ubuntu and let it do the normal set up and an Ubuntu logo appears and this orange bar starts bouncing back and forth in a loading bar. After a few minutes, the loading bar will start loading but when it reaches the end, the screen turns black and that's it. Nothing else happens. What's wrong??[/COLOR]

---

### Post by Celauran on 2009-06-17
Could be a display driver issue. Did you test drive with a live CD first? Did that work OK?

---

### Post by ryan.megatron on 2009-06-17
[COLOR="SeaGreen"]I just tried the read-only option off my Live CD and nearly the same thing happened. It loaded up just like before except instead of going to the black screen after loading, it went to a black screen and started spitting out text and errors.

First, it showed a few lines like this:
[ 382.161515] end_request: I/O error, dev sr0, sector 1430784
[ 382.161749] Buffer I/O error on device sr0, sector 178870

and it repeated that a few times but changed the numbers. Then it displayed a few lines of *loading, *saving, *setting, stuff like that. Then some more errors like above, more loading and then went to a black screen and stopped there.

Do you know the problem?[/COLOR]

---

