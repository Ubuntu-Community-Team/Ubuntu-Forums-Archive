---
title: "What exactly is KDE-core?"
date: 2007-01-06
forum: Desktop Environments
---

### Post by wersdaluv on 2007-01-06
I have just installed KDE-core with little knowledge about it.

Know that I'm running it, I have noticed that the basic KDE applications are missing. There is no volume control, adept package manager, KTorrent, wlassistant, Kontact, etc. Also, there is nothing Kubuntu about this desktop environment. It's all about KDE 3.5.

Is it really like this or there's a problem with my desktop?

Can I get those applications without researching on every basic KDE application? Is there a single step that will do the trick? 

If you know more about KDE-core that I didn't ask above, can you tell me about it?

---

### Post by slimdog360 on 2007-01-06
Its what it sounds like, the core components in order to run kde properly, kubuntu is not just ubuntu with kde placed over the top. Its a completely different distro (to an extent) which not only comes with kde but all these other thing you speak of. Kde-core intentionally doesnt come with anything else for those who wish to build their distro from the ground up. I do this but with a server install so Ive only got the things which I want. This just means that there will be less 'clutter' within the operating system, often leading to a speed boost. The sound control package your looking for is 'kmix'.

The package kubuntu-desktop comes with all the stuff you would perhaps want. Take a look on the kubuntu site and it will show you what exactly it comes with.

---

### Post by aysiu on 2007-01-06
*kde-core* is kind of barebones KDE (well, not as barebones as *kdebase*, but barebones enough). One thing you can do is type ```
sudo apt-get install kubuntu-desktop
``` When it asks if you want to install all those packages, say no, but look at the list of the packages it wants to install. Some may jump out at you as ones you want. You can install those instead of everything.

My guess is that you want at least ```
sudo apt-get install kmix adept ktorrent kontact wlassistant ark
```

---

### Post by wersdaluv on 2007-01-07
> **aysiu said:**
> *kde-core* is kind of barebones KDE (well, not as barebones as *kdebase*, but barebones enough). One thing you can do is type ```
sudo apt-get install kubuntu-desktop
``` When it asks if you want to install all those packages, say no, but look at the list of the packages it wants to install. Some may jump out at you as ones you want. You can install those instead of everything.

My guess is that you want at least ```
sudo apt-get install kmix adept ktorrent kontact wlassistant ark
```

If I install kde-core and some apps from the code above, will the support for Kubuntu Edgy be usable for me?

---

### Post by aysiu on 2007-01-07
> **wersdaluv said:**
> If I install kde-core and some apps from the code above, will the support for Kubuntu Edgy be usable for me?
What exactly do you mean by "support"?

---

### Post by wersdaluv on 2007-01-07
I order to install an app, there are steps to follow. There are some steps that should be done only for edgy or only for dapper. The support I reffered to were the steps intended for Kubuntu Edgy.  Since this is not Kubuntu Edgy or whatever Kubuntu, what "support" can I use? Or is this Kubuntu Edgy or something like that?

---

