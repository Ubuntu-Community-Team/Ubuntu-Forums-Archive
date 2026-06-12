---
title: "Gnome and Gnome apps 'dead', KDE ok"
date: 2007-07-04
forum: Desktop Environments
---

### Post by TravMan63 on 2007-07-04
I have a fresh install of UbuntuCE 7.04 (just yesterday)
I insgtalled KDE this AM.  have been able to switch sessions/desktops with no problems.

I was editing the /etc/network/interfaces file in gnome/gedit
rebooted (because I couldn't stop eth0 from getting a ip address when I used
ifconfig eth0 down - set it to static, ip address not on local subnet... no go... but that's a different issue)

When gnome attempts to start - I get the brown desktop, and a white rectangle in the top left of screen.  I can then ctrl alt f2 etc and reboot.  The 'nautilus etc is starting does not appear'

I tried gnome 'safe mode' - same thing

Going into KDE is ok - but these gnome apps won't work:
terminal and gedit. - they start - but are unusable - can not type etc... then have to kill them..

Nothing appears broken in synaptic

Ideas?

Thanks

---

### Post by TravMan63 on 2007-07-04
Beats me what happened.
I had previously powered down... restarted etc... with no change.

I let the pc sit for an hour or so - then it started fine.  I don't think it's a heat issue because everything else was working.

>> edit - here is the cause:
kde and gnome will start - if the network cable is unplugged... plug the network cable in - and gnome (and related apps) won't  start.

If gnome is started with the cable unplugged, then the cable is plugged in - an ip address is configured via dhcp.

Interesting that the gnome related aps - as well as gnome - won't work unless the network cable is plugged in AFTER gnome is 'started'

Ideas?

---

