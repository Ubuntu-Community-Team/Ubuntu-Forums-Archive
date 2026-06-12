---
title: "Firefox &amp; Mozilla cause lock-ups on a certain website"
date: 2006-09-24
forum: Desktop Environments
---

### Post by Imek on 2006-09-24
Hey,

I'm currently working on a component for Invision Power Board, which I'm developing on my Linux laptop with Apache, MySQL and PHP installed. So far I've been using Firefox to test it and it's been working fine up until now. Just recently, though, logging into the test forum has just caused Firefox to lock up my system (even CTRL+ALT+Fx/Backspace don't work). After a few minutes Firefox simply quits and the computer starts responding again. Regular Mozilla elicits a similar response.

Now I know what you're thinking: this kid's been fiddling with the wrong dials or written some infinite loop code or something! But that's not the case; Lynx works fine with the forum, as does Firefox on my Windows desktop when I connect to it from that, and when I comment out the only PHP code that could be causing a problem (i.e. the on-login code) it still crashes. And yes, I am using the latest version of Firefox and have tried completely removing it (including configs) and reinstalling it.

EDIT: Also, logging into phpmyadmin does this too..

Any ideas?

---

