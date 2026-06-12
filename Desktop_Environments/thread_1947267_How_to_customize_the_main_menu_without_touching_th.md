---
title: "How to customize the main menu without touching the 'open with' of the contextual men"
date: 2012-03-26
forum: Desktop Environments
---

### Post by tanoloco on 2012-03-26
Hello,

in the past I successfully added a custom folder called 'scripts' onto my main menu, as shown in the screenshot attached called 'main-menu.jpg'.
This add was made by following my own [thread]("http://ubuntuforums.org/showthread.php?t=1870415") mainly based on this [howto]("http://www.remastersys.com/forums/index.php?topic=1686.0").

Basically there are some new .desktop files added into ~./local/share/applications and then you have to play around with xml files in a couple of places as explained inside the above links.

My problem now is that I've noticed that my contextual-menu shows an 'open with' list fulled by any application I added with the above method, as shown in my second attachment called 'contextual-menu.jpg'.
This means that if I add my own application called foo.desktop into ~./local/share/applications and follow the above method, then  this foo application is correctly added in my main menu but also wrongly added in my 'open with' list inside my contextual menu.

I searched how to remove entries from the 'open with' list, but apparently you have to remove them form ~./local/share/applications ! as written for example [here]("http://forum.lxde.org/viewtopic.php?f=22&t=1748") in the lxde forum.
But I **have** to have them in this path to list them on my main menu!

So: is there a way to add a custom foo.desktop application inside ~./local/share/applications without adding it to the 'open with' list of the contextual menu too?

Or otherwise is there a way to remove a foo.desktop application from my 'open with' list without removing it from my customized main menu?

I hope I've been clear enough, I know it's a little bit confusing :)

Thanks in advance

---

