---
title: "evolution exchange GAL success (corporate environment)"
date: 2008-10-24
forum: Desktop Environments
---

### Post by analog_G on 2008-10-24
I've read just about every post about evolution/Microsoft Exchange configuration.  Not many describe the details of how they achieved success.  So here is what I did.  Hope it helps.

-- Ubuntu 8.04 w/all updates as of this posting --

Here are the most important settings:

**Username:*** <domain>/<username>*
[INDENT]As previously described by other posts.
for example mine is: **napa/e0085899**
(These are the same values that I would use to log into XP)[/INDENT]
**OWA URL:** *<url>*
[INDENT]This could be anything.  I found mine by using our web access link
from the corporate website.  When I click the link I was directed to:
**[https://owa.etn.com](https://owa.etn.com)**.  So that is what I used for my OWA URL.   [/INDENT]
**Global Catalog server name:** *<good luck>*
[INDENT]You could ask IT, but in my case, IT is happier if they don't know that I'm using Linux at work.  By looking up Account settings in in Outlook (logged into XP), I found that the exchange server is listed as "CLEOHSMB12.napa.ad.etn.com".  I know that CLEOHSMB12 is a netBios name for a windows server on the company LAN (If you want any gory details of how I got netBios name resolution to work in Ubuntu, let me know).  Anyway following maheshjagadeesan's idea (post #11 [http://ubuntuforums.org/showthread.php?t=195239&page=2](http://ubuntuforums.org/showthread.php?t=195239&page=2)) I dropped the computer's name and put just the domain: **napa.ad.etn.com**.[/INDENT]

After this my email, calendar and address look-up are working.

---

