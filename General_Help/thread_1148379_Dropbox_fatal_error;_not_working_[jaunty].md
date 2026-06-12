---
title: "Dropbox fatal error; not working [jaunty]"
date: 2009-05-04
forum: General Help
---

### Post by nimajiman on 2009-05-04
Has anyone else had problems getting dropbox to work properly on Jaunty? I downloaded nautilus-dropbox package from the jaunty repository as specified here [[http://www.getdropbox.com/downloading?os=lnx]](http://www.getdropbox.com/downloading?os=lnx]), then restarted X and ran dropbox from 'Applications -> Internet' which started the proprietary daemon download.

As far as I'm aware all the install steps were followed correctly however the dropbox icon appears for only a second in the notification area before disappearing again as soon as I move my mouse near it.

I tried starting the dropbox daemon from terminal with 'dropbox start' and again the icon appears for only a second with the message 'Starting Dropbox...Done!' but only until I move the mouse near the notification area like before. The icon disappears and with terminal open I get this error message:

"dropbox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0."

Anyone have any ideas why this would be happening? It worked fine for me in Intrepid. I did a clean install of Jaunty so no conflicts from an upgrade.

Cheers

---

### Post by binbash on 2009-05-04
[http://www.ubuntu-inside.me/2009/05/howto-get-dropbox-working-on-ubuntu.html](http://www.ubuntu-inside.me/2009/05/howto-get-dropbox-working-on-ubuntu.html)

---

### Post by nimajiman on 2009-05-05
> **binbash said:**
> [http://www.ubuntu-inside.me/2009/05/howto-get-dropbox-working-on-ubuntu.html](http://www.ubuntu-inside.me/2009/05/howto-get-dropbox-working-on-ubuntu.html)
Thanks for the tip. I reinstalled nautilus-dropbox from the repository to try out the experimental build in the linked post but didn't need to in the end - this time it installed fine the standard way. Maybe they updated their package overnight?

Anyway, thanks again. Great site for ubuntu tips by the way!

---

### Post by fero5 on 2009-09-19
jaunty :
this worked for me
[http://www.eyedealab.com/blog/tips-tricks-computer/solved-a-dropbox-install-error-in-ubuntu-jaunty-easily/](http://www.eyedealab.com/blog/tips-tricks-computer/solved-a-dropbox-install-error-in-ubuntu-jaunty-easily/)
... right click on networking ... disable networking
... applications - internet - dropbox
... setup dialog show up
... enable networking
... retry connection  in dropbox setup
... and continue in setup

---

### Post by Findarato on 2009-09-19
> **fero5 said:**
> jaunty :
this worked for me
[http://www.eyedealab.com/blog/tips-tricks-computer/solved-a-dropbox-install-error-in-ubuntu-jaunty-easily/](http://www.eyedealab.com/blog/tips-tricks-computer/solved-a-dropbox-install-error-in-ubuntu-jaunty-easily/)
... right click on networking ... disable networking
... applications - internet - dropbox
... setup dialog show up
... enable networking
... retry connection  in dropbox setup
... and continue in setup

Thanks m8, this worked like a charm :P

---

