---
title: "Amnesia on Steam won't launch."
date: 2012-12-22
forum: Gaming &amp; Leisure
---

### Post by RedMartin on 2012-12-22
When I launch Amnesia from the Steam beta I get a blank/see-through window called Amnesia: The Dark Descent Launcher but there is nothing in it and nothing further happens.

I tried updating my Nvidia drivers but still nothing. There are no error messages either.

Any ideas?

---

### Post by Open and Sourced on 2012-12-23
My friend, you have to run WINE. 

Otherwise you have to retain the fact that Linux was NEVER suppose to run games.

---

### Post by Artemia on 2012-12-23
RedMartin, The launcher issue from steam link is a know bug. There is a workaround who consist to launch the game binary directly from the console:
```

~/.steam/root/SteamApps/common/Amnesia The Dark Descent/Amnesia.bin

```Have now to wait an update for steam. Hope this tips will help you ):P

---

### Post by RedMartin on 2012-12-23
Actually found another cure. Simply uncheck the Enable Steam Community option.

Launcher worked a treat after that.

---

### Post by holastickboy on 2012-12-23
> **Open and Sourced said:**
> My friend, you have to run WINE. 

Otherwise you have to retain the fact that Linux was NEVER suppose to run games.

This is simply incorrect with both points made. 

1) Amnesia does work on Linux, in fact it was native to linux before even steam came along (look at the Ubuntu software center, or even check out past Humble bundles, it's all there). Your statement is completely false as it's been native even since the original release of Windows and Mac clients. There has NEVER even been a time where you have had to use WINE to run Amnesia...

2) Stating that Linux was never meant to run games is also a weird statement.  When it was first made in the early 90s it was also not meant to do almost everything it does now (including being a web server, and last time I checked more web servers run Linux than any other operating system...)

I've noticed that you have stated on other topics in these forums the same thing; it's just not true, and doesn't do anyone any good to be spreading things that are simply not true.  Windows wasn't made for gaming when it was first launched too, but it has had numerous fixes and improvements over the years to get it to where it is today (and this is the same process that is being done in Linux currently). The fact is the Linux can play games very well (and Valve has made numerous posts about how much faster things like Left 4 Dead run better on Linux than Windows), but we haven't seen many  commercial games on the platform for financial reasons, not because it's  not mean to, or because it's more difficult (because it simply isn't).

To the original poster, good to see you got it running.  I've played it through from a previous Humble Bundle purchase and it's a damn good game! Scary as all hell too!

---

### Post by vasa1 on 2012-12-23
> **holastickboy said:**
> ...
I've noticed that ...
I've noticed that as well. A lot of posts made in the space of a couple of hours.

---

### Post by madinc on 2012-12-28
> **Open and Sourced said:**
> My friend, you have to run WINE. 

Otherwise you have to retain the fact that Linux was NEVER suppose to run games.

Are you serious do you know what you are talking about i don't have WINE installed and Amnesia runs perfectly if you are on a 32bit pc the only thing you have to do to play Amnesia is install it but if you are on 64bit pc then you have to run this extra command first:

```
sudo apt-get install ia32-libs lib32nss-mdns
```and on 64bit this is needed for more games not only Amnesia.

If Linux was NEVER suppose to run games then this [http://www.ouya.tv/](http://www.ouya.tv/)
and this [http://www.ign.com/videos/2012/12/11/news-valves-console-killer-plans](http://www.ign.com/videos/2012/12/11/news-valves-console-killer-plans)
would never happen.

---

