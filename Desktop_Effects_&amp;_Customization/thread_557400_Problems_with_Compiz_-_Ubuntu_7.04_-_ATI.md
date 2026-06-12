---
title: "Problems with Compiz - Ubuntu 7.04 - ATI"
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by otafu on 2007-09-22
Hi, I am a begginer in Ubuntu, and I tried to install compiz in my laptop but didnt success.

I have an AMD64 Athlon with a ATI Radeon Xpress 200M graphics card.

I followed a howto on the net with no problems. When I finished downloading and installing, I tried to run compiz but instead, the error shows:

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

I am not sure what the error could be. I now have compiz installed but obviusly is not working.

My questions are: 
1) How can I fix the error so I try compiz?
2) How do I remove my actual compiz installation files in case its damaged or messed up?
3) After I installed compiz, I also installed the Flash player plugin for Firefox. In the howto I followed, it said that, as Adobe doesnt have a Flash player for 64 machines, first I should installed some packages to run 32 machine's applications. Could this be affecting compiz?

Thanks a lot for the opportunity to clear my doubts!

Greetings to all and thank you for any help. :D

Otafu

---

### Post by FunkyRider on 2007-09-22
The answer is that current versions of fglrx drivers doesn't yet support AIGLX, which is needed by Compiz to enable desktop effects.

However there is a workaround for this: use XGL Server.

[http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty](http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty)

---

