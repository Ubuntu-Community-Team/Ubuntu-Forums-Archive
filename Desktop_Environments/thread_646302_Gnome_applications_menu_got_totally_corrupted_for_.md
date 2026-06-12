---
title: "Gnome applications menu got totally corrupted for no reason!"
date: 2007-12-21
forum: Desktop Environments
---

### Post by mocha on 2007-12-21
Has anyone ever seen the Gnome applications menu get totally corrupted for no reason?  I've been running Feisty since it was released.  Just yesterday I go to reboot my machine and when it came back to the desktop the menus were totally screwed up.  Half the items were named "alacarte-menu-xx" and there was a bunch of links missing.

I finally fixed this by going into applications.menu file and renaming the "alacarte-menu-xx" entries to what they were supposed to be named.  I also had to change the <directory> tags within that file to the same display name that I wanted to see on the menu.

It appears that a bunch of the .desktop files somehow got crosslinked with each other and the applications.menu file was also pointing to all the wrong files.

I have absolutely no idea how this happened and it greatly concerns me, and the stability of Ubuntu in general comes into question when fundamental things like the menuing system are apparently so easy to corrupt without any input from the user.

I searched around Google and these forums and it doesn't seem like anyone else ever had this happen before.  That is why I am making this post to gather comments.

---

### Post by MC_LA on 2007-12-21
I'm having the same problem, only when I click on Applications, I get nothing. Places and System work  fine. This seemed to happen for no reason. I didn't install anything new.

---

### Post by MC_LA on 2007-12-21
so I think my problem was caused by my applications.menu getting corrupted when I was running low on disk space.  


To solve the problem, I went to the /home/<my username>/.config/menus  where I saw that I had a applications.menu file with zero bytes. I deleted the file, and then everything started working again. :-)

---

### Post by mocha on 2007-12-22
> **MC_LA said:**
> so I think my problem was caused by my applications.menu getting corrupted when I was running low on disk space.  


To solve the problem, I went to the /home/<my username>/.config/menus  where I saw that I had a applications.menu file with zero bytes. I deleted the file, and then everything started working again. :-)

I understand what you did, however when you deleted the applications.menu file a new default one was created without all of your previously installed apps, correct?  Or did all the apps you installed before magically appear in the new applications.menu file?

---

