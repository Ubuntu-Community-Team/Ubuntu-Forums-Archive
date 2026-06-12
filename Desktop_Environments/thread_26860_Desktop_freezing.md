---
title: "Desktop freezing"
date: 2005-04-14
forum: Desktop Environments
---

### Post by Wraithmonk on 2005-04-14
I like to try out various distros, so I've installed Kubuntu, & everything went well. I've also installed (via apt-get) Firefox, Gaim & Pan.
I setup Kmail, & in Appearance > System tray told it to "Enable systray icon" & "Only show Kmail in systray if there are unread messages". I also had Gaim put it's icon in the systray. 
Everything worked fine, though it did hang on shutdown. However this morning, it boots up but when it gets to "Loading the Panel" it just hangs. It's frozen, nothing I can do will unfreeze it.
I suspect that it's something to do with adding more icons to the systray, though I can't prove it, except to say that I could log in & out of the user desktop without any trouble *before* I added the systray icons, which is what led me to suspect the cause of the present problem.  
Has anyone else experienced this sort of thing? Is there anything I can do to correct this problem in Kubuntu & get it to load the desktop? 
I can boot Kubuntu to level 3 (init 3) & do any repairs from there, but I don't know where to look to correct the problem.
Normally I use SuSE, & have it on another drive, so I could access the Kubuntu drive as 'root' from my SuSE 9.2 installation & do any repairs from there too.
Does anyone any any ideas please?

I have to say that from what I'v eseen so far, I *do* like the distribution.

---

### Post by PerpetualBurn on 2005-10-05
Just checking to see if you found a way to fix this issue. I am having the exact same problem. Please let me know if you have had any success. I would greatly appreciate it.

Thanks,
Mike.

---

### Post by mlomker on 2005-10-05
I know for certain that **rm -fr /home/*username*/.kde** will solve the problem but I'm still searching for something more elegant (and that won't lose all of your customizations).

---

