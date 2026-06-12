---
title: "Gaim won't work"
date: 2006-07-04
forum: Desktop Environments
---

### Post by bobterri on 2006-07-04
I have AOL and MSN IM accounts.  Neither work with Gaim.  When I try to log on, they never connect and end up timing out.  Can anyone help?

---

### Post by st00ner on 2006-07-04
are you using moblock? i believe if its not correctly configured it can block MSN. As for aim, are you behind a corporate firewall?

---

### Post by bobterri on 2006-07-04
To be honest I don't even know what moblock is, so I don't think I'm using it.  I may have a firewall on my wireless router.  I'll check.  Any other ideas?

---

### Post by st00ner on 2006-07-04
allright you dont have moblock if you havnt installed it. Its the linux equivalent of peerguardian. Hmmmmmm...... what version of GAIM are you using?

---

### Post by bobterri on 2006-07-04
According to synaptic it is 1:1.5.0+1.5.1cvs20

---

### Post by GTvulse on 2006-07-04
[QUOTE=bobterri]I have AOL and MSN IM accounts.  Neither work with Gaim.  When I try to log on, they never connect and end up timing out.  Can anyone help?[/QUOTE]
Are you using an ADSL modem/router? You need to check the NAPT settings, as Gaim 1.5 doesn't do NAT traversal, AFAIK. Gaim 2.0 will.

---

### Post by bobterri on 2006-07-04
I am on DSL through Qwest with an Actiontec® Wireless-Ready DSL Gateway Model GT701-wg modem.  The security settings do have NAT settings with grave warnings about shutting them down.

---

### Post by bobterri on 2006-07-05
I guess I'm out of luck!  Perhaps when Gaim 2.0 comes out I'll try it.  In the meantime, one last query--anyone else that can help?

---

### Post by GTvulse on 2006-07-05
[QUOTE=bobterri]I am on DSL through Qwest with an Actiontec® Wireless-Ready DSL Gateway Model GT701-wg modem.  The security settings do have NAT settings with grave warnings about shutting them down.[/QUOTE]
So... Probably you have enabled the firewall in the modem/router. If such is the case, you need to remap ports from the router to your box. I think a visit to [http://portforward.com/](http://portforward.com/) is in order. :-)

---

### Post by bobterri on 2006-07-05
Thanks, I'll check it out.

---

### Post by bobterri on 2006-07-05
Well, it looks like I need a static IP address.  Qwest doesn't allow this.  Any other options?

---

### Post by GTvulse on 2006-07-05
Do you mean that you can't reconfigure your modem/router to turn off the internal DCHP server and assign yourself a static address in the private subnet?

You should be able to, according to the documentation available at [http://www.qwest.com/internethelp/modems/gt701-wg/index.html](http://www.qwest.com/internethelp/modems/gt701-wg/index.html). (See [http://www.actiontec.com/support/broadband/gt701-wg.html](http://www.actiontec.com/support/broadband/gt701-wg.html) for the manual of your modem/router if you don't have it at hand).

---

### Post by bobterri on 2006-07-08
I am going to be gone for three weeks.  I'll check these things out.  Thanks for you help, Dradul.

---

