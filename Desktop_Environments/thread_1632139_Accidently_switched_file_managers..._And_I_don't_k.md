---
title: "Accidently switched file managers... And I don't know how to switch back!"
date: 2010-11-27
forum: Desktop Environments
---

### Post by norfair on 2010-11-27
Hi. I feel like such a newbie mentioning what has transpired, but here goes...

I noticed something in my "System Tools" that I hadn't noticed before, and clicked on it to see what it was. That being, Dolphin. 

Well, now my system has set itself to having Dolphin as the default file manager. All I did was click on Dolphin. I made no changes or asked it to be my default. And for the life of me I can't figure out how to get back to the original file manager (Nautilus, I think). 

What's so baffling is why Dolphin (and KPackageKit) would appear in my "System Tools" when I run Ubuntu/GNOME? I even tried uninstalling Dolphin via the Software Center, but that didn't do anything. 

If anyone can help getting me back where I started, I would greatly appreciate it, as I'm lost!

Thanks.

---

### Post by akand074 on 2010-11-27
Try going to System > Administration > Synaptic Package Manager. Search "dolphin" in the quick search and uninstall everything related to it. Then sure "nautilus" and make sure its installed. If it is installed, see if Nautilus is working as your default. If it's not working, then maybe try uninstalling Nautilus and then reinstalling it and restarting. Other than that I'm not sure how you did it so I'm not sure how to undo it off the top of my head. I'm sure there is some config file where you could set which file manager as your default.

Though, if you don't already have it installed, install Ubuntu Tweak (google search it and add it to your repositories or install the .deb if its provided). Its a handy tool to tweak some Ubuntu settings. Under Session Control theres a "file manager" setting, make sure it says "nautilus". Good luck.

---

### Post by norfair on 2010-11-27
Thanks for the reply. It was weird how it happened, as all I did was click on Dolphin via "System Tools" and it changed my file manager. Strange. Anyway, after uninstalling Dolphin and that still not fixing things, I restarted my computer as per a comment of yours, and things are back to normal. I still wish there was a spot via "Administration" where one could verify/select their file manager. 

Oh, and thanks for mentioning Ubuntu Tweak. I had the installed and used it a bit on my old system. I forgot about it.

Thanks again!

---

