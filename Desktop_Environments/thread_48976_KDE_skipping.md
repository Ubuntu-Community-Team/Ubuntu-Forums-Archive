---
title: "KDE skipping?"
date: 2005-07-14
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-07-14
I never got this problem earlier, but KDE is skipping on me.  What will happen is it will freeze for about 1/2-1 second, and it happens every 10-30 seconds.  This happens alot less when I am just browsing, but it usually ends up with me typing and then it freezing in the middle of a word, then the rest to appear a second laterd (usually messed up as I hesitated after i saw the freeze).  

This happens alot more in gaming, I sas as I was playing Quake 2 (which is working now, thanks for all your help).  It freezes every 5-10 seconds, which is annoying as hell.  I played 3 levels of it like this, and I can't play with it any more.

My friend told me to do ps uax in terminal to see how many processes I was running, and he said the problem is that I am using KDE.  He said it is too CPU intensive, and I have way too many processes running.  

Then I asked, should I  use GNOME for gaming?  and he said no, If I were you I would just boot the game in the pure X Server (or something like that, I might be confusing myself here...).  How would I do this, or how would I simply turn off all the uneeded processes?  and which processes are uneeded?  I saw a few I probably don't need, such as "kjournald" which I have never used, save maybe one time just to preview all the applications kde has.

Can someone help me out with this skipping problem in KDE, or tell me how to boot the games up like he said?

---

### Post by varunus on 2005-07-14
Skipping like that?  What are your system specs?  You shouldn't be seeing that much skipping in either KDE or GNOME unless your computer is a little lower end than they're designed for...If so, I'd recommend getting XFCE and giving it a try.  But one thing to do, would be to open the system monitor and watch your CPU usage.  Does any program have a high CPU usage when the jumps occur?

---

### Post by elsewhere on 2005-07-14
If you're running with any sort of cpu frequency scaling on your system, try disabling it (ie. *sudo /etc/init.d/powernowd stop*) and see if that makes a difference. Some people have experienced that problem (sporadic freezing of X), myself included, as a result of cpu scaling.

Might be worth a shot and won't cause any harm to try.

Cheers,
KV

---

### Post by arcanistherogue on 2005-07-15
Perhaps.  It might be these wierd panels.  I accidentally enabled a panel called "KasBar" and it is really annoying me.  I can't find a way to remove it, and I see no use for it.  

And as for system specs.. I don't think It should be doing this, I have an AMD 64 bit 3000+, and a high-end graphics card (6600) and 512 MB of RAM.  I'm running the i386 version of linux though, if that would really matter.

---

### Post by Seth on 2005-07-15
[QUOTE=arcanistherogue]Perhaps.  It might be these wierd panels.  I accidentally enabled a panel called "KasBar" and it is really annoying me.  I can't find a way to remove it, and I see no use for it.  

And as for system specs.. I don't think It should be doing this, I have an AMD 64 bit 3000+, and a high-end graphics card (6600) and 512 MB of RAM.  I'm running the i386 version of linux though, if that would really matter.[/QUOTE]
 Right-click panel > Remove from panel > Panel... > Kasbar.

---

### Post by arcanistherogue on 2005-07-15
[QUOTE=Seth]Right-click panel > Remove from panel > Panel... > Kasbar.[/QUOTE]

Removing the KasBar actually solved my problem.

Thanks alot!

---

