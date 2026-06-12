---
title: "software center installation list and automation"
date: 2011-01-31
forum: Desktop Environments
---

### Post by ashwinipn on 2011-01-31
Hi,
I want to generate a list of softwares installed through Ubuntu Software Center (or synaptic) in my current installation. I also think that if I am able to save such a list in my home folder, how to execute that list either in software center or through terminal to automatically install (including connecting repositories and installing keys) when I upgrade. I know there are few things to be taken care of in such automation, such as, distribution specific modification in repository paths. This way, I don't have to every time build my system from scratch. Although most of the softwares required would be left in the folder in the home directory which I installed separately, but I have to each time connect various repositories and install softwares to make them work when I upgrade (I always do clean upgrade, never face any functionality or instability problem with this practice). The Software Center records history completely. So, if that history can be used to generate a list file, might be the point to start.

I understand that Canonical can't enable many a repositories and functions by default because of the open source philosophy behind, but if a user can save these softwares as a list, later the process can be automatized on individual basis. This will greatly save time and will be useful in any OS or hardware upgrades. Suggestions and ideas for making it a reality for me is welcome.
Cheers...

---

### Post by 101011010010 on 2011-01-31
Hello, For a list of installed applications and to install, try this:

> [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)When you've added the Repositories that you want (on your current install), navigate to "/etc/apt" and copy the "sources.list". Next time you do a clean install/upgrade put your "sources.list"in /etc/apt,(over write the existing one) and then use the installed application list and everything should be how you want.
I hope this helps.

---

### Post by ashwinipn on 2011-01-31
> **101011010010 said:**
> Hello, For a list of installed applications and to install, try this:

When you've added the Repositories that you want (on your current install), navigate to "/etc/apt" and copy the "sources.list". Next time you do a clean install/upgrade put your "sources.list"in /etc/apt,(over write the existing one) and then use the installed application list and everything should be how you want.
I hope this helps.

Thanks for your suggestion. Yes I will do that now onwards.... But I have to manually modify /etc/apt/sources.list file for it to be distribution specific. That is however an easy job. But how do I know what all softwares were installed in the previous machine? Where do I get this installed application list on my current system?
Thanks...

---

### Post by 101011010010 on 2011-01-31
Hello, Open a terminal (Applications/ Accessories/ Terminal) and copy and paste this command into the teminal and press Enter:

> dpkg --get-selections > installed-software A file called "installed-software" will be created in your Home folder.
Follow the instructions in the link to reinstall the applications.
A.

---

### Post by ashwinipn on 2011-01-31
> **101011010010 said:**
> Hello, Open a terminal (Applications/ Accessories/ Terminal) and copy and paste this command into the teminal and press Enter:

 A file called "installed-software" will be created in your Home folder.
Follow the instructions in the link to reinstall the applications.
A.

Thanks for your reply and sorry for overlooking the link in your first response.... just concentrated on your reply outside the quote... may be because of my habit of overlooking quotes (most of the times quoted for the specific contextual reply only). This is exactly in the line I was thinking. I will get back to home and try this out and update about the progress.
Thanks a ton.

---

### Post by 101011010010 on 2011-01-31
Hello. 
No problem, I hope it works the way you want.
A.

---

