---
title: "ARTS crashing"
date: 2005-10-22
forum: Desktop Environments
---

### Post by Navyblue on 2005-10-22
Hi all,

This is in no way a serious problem, but just annoying.

Sometime right after booting up and entering KDE, the startup sound which it supposed to sound didn't sound, CPU activity would be at 100%, and after a while a window would pop and says ARTS crashed and ask me to click "OK". However, my sound would still work. It does not happen all the time, may be half of the time.

I have chosen ALSA for everything, and have unistalled ARTS thinking that the problem would go away. However, the phantom ARTS pop up still appear every now and then.

What is likely wrong here? Would it be a hardware problem since it only happen some of the time?

I recall during my M$ days the Creative Control Centre would pop up once in a while saying that no Creative Control Centre compatible sound card is detected (or something to that effect) and asked me to click the dang "OK". However, the sound would still work.

I don't remember it appearing in 32 bit Hoary.

I am running Creative Live! Value on 64 bit Kubuntu btw.

Thanks for reading. :)

---

### Post by Navyblue on 2005-11-04
No one has this problem?

---

### Post by shinygerbil on 2005-11-04
Have you upgraded to the KDE3.5 beta?

---

### Post by Navyblue on 2005-11-04
Nope, I am running KDE 3.4. Btw I am running 64bit version of Ubuntu, KDE 3.5 is not available.

---

### Post by shinygerbil on 2005-11-04
<-- shinygerbil = stupid ;)


I had something else similar to this problem, which was entirely caused by me being impatient. Whenever I booted up my PC, as I use a wireless connection and nothing's plugged into the ethernet port, the bootup would take about 30 seconds to get past "Configuring network interfaces..." 

So I had the bright idea of hitting Ctrl+C to skip this long and boring wait. As soon as I did that, the ALSA stopped working, so I guess my fiddling/impatience messed around with loopback stuff. (i.e. the section of /etc/network/interfaces that has all the 'auto lo' stuff)

It's just an idea - probably not correct but you never know...

Steve

---

### Post by Navyblue on 2005-11-04
For my case, I didn't do anything, no key press no nothing. You'll know it when it happen, there is no startup sound, and some time later the error message window would pop up. Enemy territory caused X to crash quite often for me, not sure if it is sound related too.

---

