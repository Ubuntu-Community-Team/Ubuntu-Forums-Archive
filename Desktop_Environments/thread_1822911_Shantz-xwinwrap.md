---
title: "Shantz-xwinwrap"
date: 2011-08-11
forum: Desktop Environments
---

### Post by tedribon on 2011-08-11
Hi all, i've been trying to get shantz-xwinwrap installed on my new pc, but i'm a fresh off the boat when it comes to Ubuntu. All i get is the result below.

[COLOR=Red]Lintian check results for /home/ted/shantz-xwinwrap/x86_64/shantz-xwinwrap_0.3-1_amd64.deb:
E: shantz-xwinwrap: wrong-file-owner-uid-or-gid usr/ 1000/1000 
E: shantz-xwinwrap: wrong-file-owner-uid-or-gid usr/bin/ 1000/1000 
E: shantz-xwinwrap: wrong-file-owner-uid-or-gid usr/bin/xwinwrap 1000/1000 

[COLOR=Black]When ignore the above message i get the following result;[/COLOR]

(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 169100 files and directories currently installed.) 
Unpacking shantz-xwinwrap (from .../shantz-xwinwrap_0.3-1_amd64.deb) ... 
dpkg: error processing /home/ted/shantz-xwinwrap/x86_64/shantz-xwinwrap_0.3-1_amd64.deb (--install): 
 trying to overwrite '/usr/bin/xwinwrap', which is also in package xwinwrap 0.2-0~getdeb1 [/COLOR]

Any ideas? I would appreciate any input. I've been trying to get an animated desktop working without getting it minimized when hitting the "Minimize all windows/Show desktop" button on the bottom left corner. Also, if anyone could tell me how to get the desktop animation to stick on the autostartup i would be a happy camper.

Kind regards/
Ted Ribon

---

### Post by |Anthony| on 2011-11-03
I wrote a pretty lengthy bash script (500+ lines) as a frontend for  xwinwrap. It has the autostart feature you are looking for. Also gives  you the ability to set transparency and and adjust the volume (for  videos) among lots of other features. I haven't figured a way to keep it from minimizing with the "Show Desktop" button, but conky suffers from that annoyance too so I think we'll have to deal with it :/ .  It's called VDesk and you can get  it for free at [gnome-look]("http://gnome-look.org/content/show.php/VDesk+-+Visual+Desktop?content=141678"). Enjoy and you're welcome. :smile:

---

