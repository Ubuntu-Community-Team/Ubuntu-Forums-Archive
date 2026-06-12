---
title: "Content/Parental Controls for Schools"
date: 2023-12-04
forum: Education &amp; Science
---

### Post by reformed-skiddie on 2023-12-04
Hi, what do you think is the easiest-to-use FOSS system for parental / content control at the moment?

I have Edubuntu 23.10 installed on a set of  computers in a very cash-strapped school here (some with 23.04 still to upgrade), and we would *ideally* like to install one program that can block inappropriate content across other programs (e.g. both Firefox and Chromium, and anything else that can load remote content), and be managed from the admin account such that an unprivileged student account cannot mess with it.
Otherwise we may need to subscribe to an expensive blocking system at the router.

I looked at the [Parental Controls]("https://help.ubuntu.com/community/ParentalControls")  Ubuntu help page, but it is *horrendously* out of date, as some of the systems recommended there have broken links or are over a decade old!
On searching this forum for parental controls, all the relevant threads I saw were several years old too, so I hope it's ok to make this one.

Is there any easy-to-use current solution to that, like WebContentControl was supposed to be in 2010? ...or must we  suffice with separate browser extensions only?
For comparison, Sophos offer a freemium desktop software solution to  control  this for ***dows and M*c, but sadly they do not  offer a GNU  version.

If using browser extensions, how can we protect them from tampering? For example, FoxFilter was recommended, which technically has that capability, but it runs on a freemium model that requires a subscription in order to password-protect the add-on settings for just one browser, requiring a higher fee for the multiple computers that we have, so I'd like to look at options that don't need approval from finance first, especially if it's on a per-browser basis.
**Edit:** it seems that FoxFilter is also available for Chrome and *dge, and as an iOS app, but perhaps not Safari on old hardware. I'll look more into this.

Thanks for your time!

---

### Post by TheFu on 2023-12-04
I don't know of any "easy to use" items, but if you can control DNS, you can use free DNS filtering services or run your own pi-hole to filter using content lists under your control.  Millions of people run pi-hole software, so it can't be THAT hard, but it isn't something I'd try to talk a grandmother into doing.

Also, there are lots of ways around DNS filters, so if you need absolute control without any ways around it, you'll need to pay someone who understand proxy servers and default routes configured in a way that ZERO traffic gets to the internet that doesn't actually go through the proxy server.  This method removes the ability for any client system config changes to bypass blocks.  Period.   Basically, you'd setup squid as a transparent proxy and only have the squid server given access to DNS, no clients.

---

