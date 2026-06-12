---
title: "To update or not to update, that is the question."
date: 2009-01-03
forum: General Help
---

### Post by onemanwaking on 2009-01-03
Hey everyone,

In my past experience with setting my parents, my aunt and myself up with Ubuntu laptops, I´ve often run into trouble whenever the system updates with new kernel headers. Sometimes it would go OK, but many times things break, such as wireless, sound, screen resolutions, etc. I was able to get into the grub menu config file and comment out the offending kernel, but this is not the type of thing that is easy to explain to an Ubuntu newbie over the phone.

I am now in a dilemma.

I am beginning a spare time project that helps senior citizens acquire and learn about computers and the Internet. Of course, the OS of choice is Ubuntu, and the reasons should be obvious. As part of the package, I offer a year of free phone support because of the maintenance-free nature of Linux. But these kernel update problems could spell disaster for my business. I can just imagine dozens (maybe more) of people phoning me with reports of all manner of problems caused by a new kernel update. This would be a nightmare to explain to a senior citizen and would probably require me to travel to many locations in order to fix the problems. It wouldn´t help to instill confidence in a new Linux user either.

So, I´m wondering if it might be less of a hassle to turn off updates altogether? Which is the lesser evil? Would the system still perform well one or two years from now without experiencing any updates, or am I asking for even more trouble?

I really need some advice here! Thanks!

---

### Post by ByKeLaO on 2009-01-03
I must say I've never run into such problems :S
Have you perhaps enabled the unsupported updates ("intrepid-proposed") in synaptic? That has caused problems for me in the past.

In answer to your original question: I would not recommend disabling automatic updates as in most cases they improve things rather than breaking them. However, I am of the opinion that Kernel updates aren't worth installing unless they fix something that was previously broken. For example, I would install a Kernel update if it allowed me to stop using ndiswrapper to get wireless working, but not if the update provided improved support for devices I don't have.

---

### Post by onemanwaking on 2009-01-03
OK, but is it possible to turn off just the kernel header updates? I thought they were considered part of the "Important security updates"? Maybe I'm wrong...

My goal is to set these systems up so that the update process was as easy to execute for senior citizens as possible. Example: click the notification icon, then click OK in the Update Manager and enter your password. Easy. The problem is that so many of these updates appear with cryptic names that would be difficult for most people outside of the Linux savvy to interpret, so if these users could just agree to everything that was recommended, that would be the least amount of stress for them.

Again, any suggestions are appreciated, thanks!

---

### Post by ByKeLaO on 2009-01-03
What you *could* do is teach them what to do if an update goes wrong. Tell them to press Escape while their computer is booting and choose a different kernel option in the list.
If you enable the savedefault option in GRUB then the system will automatically boot the kernel they chose, and so they'll be OK until another kernel update comes along.

---

### Post by onemanwaking on 2009-01-03
> **robinjam said:**
> What you *could* do is teach them what to do if an update goes wrong. Tell them to press Escape while their computer is booting and choose a different kernel option in the list.
If you enable the savedefault option in GRUB then the system will automatically boot the kernel they chose, and so they'll be OK until another kernel update comes along.

I thought of that, sort of. My thought was to provide them with the Startup Manager utility, which makes choosing a bootup kernel a fairly simple, graphical process - and one that they would only have to do once. I suppose I could do this in the interim, until I figure out how to limit or ignore just the kernel updates.

To be honest, I haven't had a kernel issue in a while. They seemed to be more prevalent back with Dapper, Edgy and Feisty. Is it possible the Ubuntu team have developed a better quality control for these types of things? Maybe I'm worrying too much...

Thanks again, robinjam.

---

### Post by ByKeLaO on 2009-01-03
I think it's the Linux kernel developers that we have to thank for that. Kernel updates do seem to break things much less often now than they did a couple of years ago.

---

