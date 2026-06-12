---
title: "dyndns and ipcheck at startup"
date: 2005-12-05
forum: Desktop Environments
---

### Post by PokerFacePenguin on 2005-12-05
I installed and configured the ipcheck .deb from the repos to get dyndns going.  Basically, it is a python script that outputs a some files in the directory it runs from.  I don't want to trash up my /etc/init.d directory with this extra fluff.

  [LIST=1]
[*]What is the best way to run this script at startup script without trashing up my /etc/init.d?
[*]  Does the actual python script have to be able to take a parameter (start) if in /etc/init.d with a symlink from /rcX.d? 
[*]  Would runlevel 2 be the appropriate place?
[/LIST]

---

### Post by z-vet on 2005-12-05
[This](http://www.justlinux.com/nhf/Distribution_Specific/Debian_GNULinux/Debian__Startup_Commands.html) may be helpful.

---

### Post by PokerFacePenguin on 2005-12-05
Thanks for the nice link.  Looks like it will be a nice alternative to trashing up the default locations.

---

### Post by ltmon on 2005-12-05
There's a part of [http://ubuntuguide.org](http://ubuntuguide.org) that describes doing this.  It uses a cron job to update your IP hourly, rather than just on startup.

I found that it worked fine for me.

L.

---

### Post by PokerFacePenguin on 2005-12-06
[QUOTE=ltmon]There's a part of [http://ubuntuguide.org](http://ubuntuguide.org) that describes doing this.  It uses a cron job to update your IP hourly, rather than just on startup.

I found that it worked fine for me.

L.[/QUOTE]
Nice...an even better solution not to cut me off from my ssh remote.  Hmm...I could even get more eloquent with this and turn it on an off periodically....if ps aux | grep me on a ssh session....turn it off until next interval...hmm.
*wheels turning*

---

