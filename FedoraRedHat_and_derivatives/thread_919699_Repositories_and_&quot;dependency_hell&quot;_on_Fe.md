---
title: "Repositories and &quot;dependency hell&quot; on Fedora 8"
date: 2008-09-14
forum: Fedora/RedHat and derivatives
---

### Post by motoperpetuo on 2008-09-14
I've been using Ubuntu and Mint for well over a year now, but I figured I'd give Fedora a try, mainly because most companies that use Linux seem (as far as I can tell) to use Red Hat, so I figured getting familiar with Fedora might help me in my quest to eventually do more Linux and less Windows at work. Since I happened to have a Fedora 8 DVD sitting around, I went ahead and installed it on my old laptop.

I think I'm running into this "dependency hell" of which I've heard rumors, and with which I never really had problems in Ubuntu and Mint. Basically, I'm constantly getting errors about missing dependencies when trying to install software, and even when trying to install updates that the system recommends. 

I'd read early on the you shouldn't enable both the livna and freshrpms repositories because they conflict, so i didn't do that. However, I did enable livna and atrpms. After doing so, I read a few things that suggested that you should only enable one third-party repository, otherwise you're asking for conflicts that lead to errors just like the ones i've been getting.

so, my questions are these: 

1) is it really best to choose just one third-party repository?

2) if so, which one is best? livna? freshrpms? atrpms? something else?

3) since i suspect that i've screwed things up by downloading conflicting versions of packages, is there any way to clean things up? or, would i be better off just reinstalling and starting from scratch?

---

### Post by exploder on 2008-09-14
It is best to stick with one third party repository. I chose livna and got everything I needed with no problems. I only had to get libdvdcss2 from rpm search.

---

### Post by Antman on 2008-09-14
> **motoperpetuo said:**
> I've been using Ubuntu and Mint for well over a year now, but I figured I'd give Fedora a try, mainly because most companies that use Linux seem (as far as I can tell) to use Red Hat, so I figured getting familiar with Fedora might help me in my quest to eventually do more Linux and less Windows at work. Since I happened to have a Fedora 8 DVD sitting around, I went ahead and installed it on my old laptop.

I think I'm running into this "dependency hell" of which I've heard rumors, and with which I never really had problems in Ubuntu and Mint. Basically, I'm constantly getting errors about missing dependencies when trying to install software, and even when trying to install updates that the system recommends. 

I'd read early on the you shouldn't enable both the livna and freshrpms repositories because they conflict, so i didn't do that. However, I did enable livna and atrpms. After doing so, I read a few things that suggested that you should only enable one third-party repository, otherwise you're asking for conflicts that lead to errors just like the ones i've been getting.

so, my questions are these: 

1) is it really best to choose just one third-party repository?

2) if so, which one is best? livna? freshrpms? atrpms? something else?

3) since i suspect that i've screwed things up by downloading conflicting versions of packages, is there any way to clean things up? or, would i be better off just reinstalling and starting from scratch?

I have been using Fedora on and off since Werewolf (verison 8 ) and I have yet to encounter 'dependency hell'. As long as you don't mix third party repos, you'll be fine. I have always used Livna with no issues.

---

### Post by motoperpetuo on 2008-09-14
thanks to both of you for your replies. i'll remember to stick with one third-party repository in the future, probably livna, since you and others i've talked to have spoken of it highly.

as for my third question, is there any good way to repair the damage that i've probably already done by enabling livna and atrpms? this is, any way to tell which packages i've gotten from atrpms and get rid of them? or should i just reinstall fedora and be more careful next time?

---

### Post by exploder on 2008-09-14
I would just start over with the new information you have. You will be happy with the end result.

---

