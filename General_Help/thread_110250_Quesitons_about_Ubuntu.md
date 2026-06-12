---
title: "Quesitons about Ubuntu"
date: 2005-12-30
forum: General Help
---

### Post by MrSky on 2005-12-30
I really like ubuntu and was wondering if anyone can help me to become "windowsless". If there is anything (books, websites) i can learn from, plz provide the address as well, thx.

1.   how do you install programs that's not in the "add program" list?
2.   how do you install ".rpm" and ".run" and compressed files?
3.   how do you install plugins for firefox?
4.   how do you install/upgrade drivers?
5.   how do you create a new folder?
6.   Is there a "task list" program where i can see what programs are running and maybe close freezed one one?
7.   Is it possible to do a "Home Network" with another windows machine through router?
8.   how do you change display resolution/color?
9.   When i click on my floppy drive, it says "unable to mount the volume"

That's it for now, if anyone can answer any of the above question, plz do so and i thank you.

---

### Post by Susana on 2005-12-30
1. Alt+F2 gksudo synaptic (or system->administration->synaptic) you should try to install very program using synaptic
2. alien -i filename (you need to install alien from synaptic first)
3, 4, 7  [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)
5. mkdir newfolder (in terminal) or right click-> create folder
6. in terminal: ps -xu or top, to close a freezed program: kill -9 'pidof program-name'
8. system->preferences->screen resolution
9. try sudo mount /media/floopy, when you're done umount /media/floopy

nice list! if you need more detailed help just ask.

---

