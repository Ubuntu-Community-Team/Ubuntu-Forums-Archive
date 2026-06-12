---
title: "not loading at start up"
date: 2009-02-25
forum: General Help
---

### Post by Dinusor on 2009-02-25
Hi,

I have just installed Ubuntu (i'm new with linux) on my laptop. I upgraded the system and now I have problems when starting, thus: 
after the screen which let me chose between ubuntu and windows appears, and i choose Ubuntu, the loading bar appears, with "Ubuntu" on top. But after is finished loading, the login screen dose not appear anymore, just the mouse cursor  showing that something is loading, on a black background...and just that, i can not do anything. Before installing some packages (like, orbit2.0, gmodule 2.0, dbus, gnome 2.20, etc) everything was fine,:).

I used the recovery mode, and i used "Drop to root shell prompt" option. I have stoped gdm and then started again and the same problem appeared. I also tried startx but i got an error that "waiting for X server to shut down" (this to be the problem? that is waiting X server to shut down? does it make sense?8-[)

I have also used the option to "dpkg" tp repair broken packages and i got this:

cannot remove /var/lib/apt/lists/partial/*: No such file or directory
cannot remove /var/cache/apt/archives/partial/*: No such file or directory
Then asking if i want to upgrade, and founds that intltool should be upgraded but can not do it because my internet conection

Hope that somebody can clue me what to do, thanks alot!

---

