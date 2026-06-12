---
title: "using jwm instead of xfce"
date: 2007-08-23
forum: Desktop Environments
---

### Post by coldleg on 2007-08-23
hi

i'm using xubuntu 7.04 on a quite old computer. i works, but gets slow when i have more programs running.

is it a good idea to switch to JWM?

---

### Post by Tux Aubrey on 2007-08-23
Sounds like multi-tasking overload is your issue, rather than the Desktop Environment.

I find JWM very clunky - you _could_ install fluxbox from the repositories and try it as a different session (that's how it will appear - as an alternative session available at the logon screen).  Its lighter than Xfce but not (IMO) as difficult and obscure as JWM.

You will need to read up on configuring fluxbox (or JWM) before you use it - the default setup is very lean and un-functional.  There area few good fluxbox how-tos around.  Try [here.]("http://wiki.fluxbuntu.org/Fluxbox")

---

### Post by kerry_s on 2007-08-23
> **coldleg said:**
> hi

i'm using xubuntu 7.04 on a quite old computer. i works, but gets slow when i have more programs running.

is it a good idea to switch to JWM?

jwm is nice, once you get use to it you realize how simple it is. i compiled a current version from the jwm site.

[http://ubuntuforums.org/attachment.php?attachmentid=40588&d=1187045516](http://ubuntuforums.org/attachment.php?attachmentid=40588&d=1187045516)

your going to need to install libjpeg62 (sudo apt-get install libjpeg62) i added jpg support.

---

### Post by coldleg on 2007-08-23
it is possible to use the files and programs wich i have now on jwm or fluxbox too?
or do i have to install them again??? because i'm quite lost without synaptic

---

### Post by kerry_s on 2007-08-23
> **coldleg said:**
> it is possible to use the files and programs wich i have now on jwm or fluxbox too?
or do i have to install them again??? because i'm quite lost without synaptic

just install jwm or fluxbox then log out and select it in the session menu and log back in. all the applications you have now will still be there. you'll have to do the menu yourself in jwm though, easy text editor action, for fluxbox run> sudo update-menus <before you switch to it.

installing a deb

sudo dpkg -i *.deb


You do know your way around a linux file system right?

---

### Post by coldleg on 2007-08-23
yes i think this won't be a problem.

i tried jwm now but if i start gaim for example, the screen turns black and i get back to the log on screen.

do you have an idea why?
i installed jwm with synaptic and did no configuration could that be a problem?

---

### Post by kerry_s on 2007-08-23
> **coldleg said:**
> yes i think this won't be a problem.

i tried jwm now but if i start gaim for example, the screen turns black and i get back to the log on screen.

do you have an idea why?
i installed jwm with synaptic and did no configuration could that be a problem?

no i don't think so, my guess would be in the 1 version in the repo the dock is not set up, i use ayttm, cause gaim/pidgin have just gotten to bloated for my tastes, so i never came across that. the 1 from the jwm site is way better he has made major improvements.

i would say copy over the jwmrc(cp /etc/jwm/jwmrc ~/.jwmrc), and set that up first in the tasklist section add " <Dock/> " so gaim has somewhere to stick the icon.

---

### Post by gatewayasteroid on 2007-08-24
> **coldleg said:**
> hi

i'm using xubuntu 7.04 on a quite old computer. i works, but gets slow when i have more programs running.

is it a good idea to switch to JWM?

Just use IceWM or Openbox and live happy!

---

### Post by urukrama on 2007-08-24
I second Openbox. There is a nice group of openbox users on these forums as well, so you'll get plenty of help if you need it.

---

### Post by coldleg on 2007-08-24
thank you all for your help i think i will try all of them.

---

### Post by urukrama on 2007-08-25
Forgot to mention: If you try Openbox, install the latest version, available at their [website]("http://icculus.org/openbox/index.php/Openbox:Download"). It contains numerous improvements over the version in the repositories.

---

