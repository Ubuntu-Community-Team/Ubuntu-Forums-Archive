---
title: "Giving Steam its own partition"
date: 2013-03-10
forum: Gaming &amp; Leisure
---

### Post by arkanabar on 2013-03-10
I've long played WoW on multiple distros using Wine.  My trick was to install all my windows software in its own partition which I would mount to ~/.wine/drive_c/Programs during startup.  This successfully isolated the Windows software for use in multiple editions of Wine, under different distros, and I didn't have to install WoW (or anything else) over again for every distro and/or release.  Since I am an inveterate distro-hopper using a shared connection with people who can get really unhappy if I hog all the bandwidth, this was important to me.

But I want to do something similar with regards to Steam, that is, have a patition dedicated to it, that can be used by multiple distros/releases.  

Where would its mount point be?  My current guess is that I could use ~/.local/share/Steam (most of the links in ~/.Steam appear to point there) but I am not sure.  

Does everything needed go in there?  

Is anything in there (or ~/.Steam) that is distro- or release-specific?  Does anybody have any thoughts?

---

### Post by ZarathustraDK on 2013-03-10
In the steam-settings you can define exactly where you want to download your games to, other partitions included.

You can't, however, delete the default download-folder, so everytime you download a game you get the option of choosing one of the 2 (or more) download-locations you've defined.

When you reinstall Steam on a new distro, just point it towards your previous download-folder and voila.

---

### Post by arkanabar on 2013-03-11
> **ZarathustraDK said:**
> In the steam-settings you can define exactly where you want to download your games to, other partitions included.

You can't, however, delete the default download-folder, so everytime you download a game you get the option of choosing one of the 2 (or more) download-locations you've defined.

No, I can't.  I can define other directories as libraries for steam, but I can't select them as the destination for a download.  They go to default or they don't go at all.

---

### Post by dmn_clown on 2013-03-11
> **arkanabar said:**
> But I want to do something similar with regards to Steam, that is, have a patition dedicated to it, that can be used by multiple distros/releases.  

Where would its mount point be?  My current guess is that I could use ~/.local/share/Steam (most of the links in ~/.Steam appear to point there) but I am not sure.

I suggest installing steam in /golfshoes/ it's as good a place as any, drives the FHS crowd crazy, and it's a constant reminder that you need golf shoes to walk in all this muck.

---

### Post by Cheesemill on 2013-03-11
Are you sure you don't get to choose where the games download to, I have this option available...

[[IMG]http://ompldr.org/taHB6dg[/IMG]]("http://ompldr.org/vaHB6dg")

---

### Post by ZarathustraDK on 2013-03-11
Yeah I get the same result as Cheesemill.

Maybe you haven't mounted the new partition before you start up Steam? I forgot to do it once and then all my installed games got greyed out (as in "not installed"); tried to install a game and I didn't get the option of choosing install-location, it just went ahead and installed to the default-location.

Closed Steam, mounted the partition, launched Steam, it worked normally again.

---

### Post by Cheesemill on 2013-03-11
It looks like this *is* an issue with some games.

I've just tried installing Counter Strike: Source and it didn't give me the option like it did with Osmos. It's probably worth raising the issue with Valve.

---

### Post by ZarathustraDK on 2013-03-11
> **Cheesemill said:**
> It looks like this *is* an issue with some games.

I've just tried installing Counter Strike: Source and it didn't give me the option like it did with Osmos. It's probably worth raising the issue with Valve.

Hmm... same here. And it isn't disk-space either.

If I had to venture a wild guess: Probably all the original Source-engine games gets installed to the default directory because they share a lot of the basic code. All games except CS-Source, TF2 and TF2 beta gives me the prompt for location.

I'd still call it a bug though, those games can be huge so that may not be a possibility for those of us who use a small, fast HD for the OS and big clunky ones for the rest.

---

### Post by Cheesemill on 2013-03-12
> **ZarathustraDK said:**
> If I had to venture a wild guess: Probably all the original Source-engine games gets installed to the default directory because they share a lot of the basic code. All games except CS-Source, TF2 and TF2 beta gives me the prompt for location.

That was ***exactly*** what I was thinking :)

I'll raise a support ticket with Valve and see if I can get an answer.

---

### Post by arkanabar on 2013-03-12
That would be it.  I was trying to install TF2.

---

