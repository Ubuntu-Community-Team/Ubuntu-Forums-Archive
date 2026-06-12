---
title: "What are the advantages of networkmanager over wicd?"
date: 2009-01-30
forum: General Help
---

### Post by wersdaluv on 2009-01-30
I just installed wicd because whenever I'm on kde, the knetworkmanager for kde 4.2 is annoying me (it's under heavy development). Also, whenever I'm in school, I have to refresh the list of available wireless networks for a few times to make sure that the list of wireless networks are updated whenever I wake my computer from sleep. Networkmanager doesn't have the refresh function while wicd has it. I also love the wicd interface better because it has a lot of options.

I'm wondering why networkmanager has always been the default app for the job. What are the advatages of networkmanager over wicd?

---

### Post by blazemore on 2009-01-30
Well I don't know about KDE, but in Gnome, network manager is useful for if you have a laptop and switch between wireless networks, or 3G networks a lot.

---

### Post by hyper_ch on 2009-01-30
I haven't liked neither gnome nor kde network manager this far and have traditionally manually edited my interfaces file. After I discovered wicd I've been using this. However it will be interesting how the networkmanagers will be in 9.04.

---

### Post by blazemore on 2009-01-30
Well I have laptop with Wireless at home, my girlfriends house and school.

---

### Post by wersdaluv on 2009-01-30
Thanks, guys. Wicd really is cool.

So, does anyone know any advantage of networkmanager? I'm more intrigued about why it's the default one. :D

I also remember that there used to be many wireless cards that work with wicd that didn't work with networkmanager

---

### Post by PreviousN on 2009-01-30
It is better integrated with the gnome desktop. I say this even though I use wicd. I would use networkmanager except for the fact that it doesn't work well with my wireless card...

---

### Post by blazemore on 2009-01-30
Basically, network manager works really well, so there's no need to change it in the default installation.

---

### Post by hyper_ch on 2009-01-30
network manager handles roaming mode better for wifi than WICD.

---

### Post by wersdaluv on 2009-01-30
> **blazemore said:**
> Basically, network manager works really well, so there's no need to change it in the default installation.
Uhmm. Any evidence?

---

### Post by wersdaluv on 2009-01-30
> **hyper_ch said:**
> network manager handles roaming mode better for wifi than WICD.
How? :)

---

### Post by Neural oD on 2009-01-30
agree with hyper_ch - sometimes doing it on the command line is still best
I sometimes have issues where I have to ifdown eth0 for my wireless to work - it's best when one knows what's going on - and not just everything done by magic.

---

### Post by imdano on 2009-01-30
NM has support for dial-up, VPN, and 3G/mobile broadband, wicd does not.  NM supports multiple connections at once in version 0.7, wicd doesn't have it yet (it's in development, though).  NM is developed by Red Hat and is well-integrated into most of the mainstream Linux distros, with lots of people making contributions to it.  Wicd is developed by two people in their free time, with contributions from a handful of others.  NM has been in development for five(?) years, wicd only two.

Some of the differences are philosophical, wicd aims to be more light-weight than NM does, which is part of the reason we've resisted relying on HAL or gnome libraries.  This means it won't be as tightly integrated with Gnome.  And since we have fewer developers and have been in development for less time, we're behind on some features and stability.  A bunch of Linux distros basically picked NM as their network app of choice before wicd even existed, so until it can match all of its features they're not going to switch.

---

### Post by bodhi.zazen on 2009-01-30
To be honest I think it is a matter of preference.

In my experience , network manager does not always work, NM, for me, will not do wireless (WPA) on my network where wicd will. I have also had a better experience with roaming and I like the way wicd has profiles.

If network manager meets your needs there is no reason to change. On th eother side if it does not -> go for network manager ;)

---

### Post by wersdaluv on 2009-01-30
> **imdano said:**
> NM has support for dial-up, VPN, and 3G/mobile broadband, wicd does not.  NM supports multiple connections at once in version 0.7, wicd doesn't have it yet (it's in development, though).  NM is developed by Red Hat and is well-integrated into most of the mainstream Linux distros, with lots of people making contributions to it.  Wicd is developed by two people in their free time, with contributions from a handful of others.  NM has been in development for five(?) years, wicd only two.

Some of the differences are philosophical, wicd aims to be more light-weight than NM does, which is part of the reason we've resisted relying on HAL or gnome libraries.  This means it won't be as tightly integrated with Gnome.  And since we have fewer developers and have been in development for less time, we're behind on some features and stability.  A bunch of Linux distros basically picked NM as their network app of choice before wicd even existed, so until it can match all of its features they're not going to switch.
Wow. This is the answer that I've been looking for. Thanks :)

---

### Post by wersdaluv on 2009-01-30
> **bodhi.zazen said:**
> To be honest I think it is a matter of preference.

In my experience , network manager does not always work, NM, for me, will not do wireless (WPA) on my network where wicd will. I have also had a better experience with roaming and I like the way wicd has profiles.

If network manager meets your needs there is no reason to change. On th eother side if it does not -> go for network manager ;)
I agree. I guess, even if nm has more features, wicd has more of the features that I actually need. :)

---

