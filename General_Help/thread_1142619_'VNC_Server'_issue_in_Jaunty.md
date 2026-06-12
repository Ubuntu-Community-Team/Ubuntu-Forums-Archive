---
title: "'VNC Server' issue in Jaunty"
date: 2009-04-29
forum: General Help
---

### Post by ivaarsen on 2009-04-29
Hello all,

I'm getting a strange effect after connecting to my 9.04 machine using VNC.  I'll explain:

I have a VPN connecting my home network to the network at my job.  It helps for remote management after hours, and provides me with another view of the internet during work hours.  Pretty handy.  I simply used the Remote Desktop applet to turn on Ubuntu's VNC server.  This was while I had the machine running 8.10 Intrepid.  

After upgrading to Jaunty, I seem to have trouble communicating with my computer using VNC.  I can see the desktop, but it doesn't appear that I can manipulate it.  When I click on say, a menu, I can't see that menu opened until I disconnect VNC and reconnect.  It seems I'm not getting a screen refresh, even when I click the 'refresh screen' button.  I had seen this while Jaunty was still in Beta, and it caused me to go back to Intrepid, hoping that would have been addressed.  Unfortunately, I'm still experiencing it.

Has anybody else encountered this issue?  Does anybody suppose this can be corrected by doing a fresh install of Jaunty as opposed to an upgrade?

Edit:  I'd like to clarify, if I can.  This is when running over the VPN from work to home.  I just tried to connect to an Ubuntu machine on the same LAN (at work) and it seems fine.  This machine has also been upgraded from Intrepid.  It would seem it's a latency issue, but I'm not so sure.  I wasn't seeing this until after the upgrade.

As always, thanks for your time.

---

### Post by Kareeser on 2009-04-29
It's a regression. Contribute here!

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126)

---

### Post by locovaca on 2009-04-29
Since there is a "workaround" (however unsatisfying it is), I'm not expecting to see this fixed in Jaunty.

---

### Post by ivaarsen on 2009-04-30
> **Kareeser said:**
> It's a regression. Contribute here!

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126)

Spot on.  Thanks much for the info!

---

