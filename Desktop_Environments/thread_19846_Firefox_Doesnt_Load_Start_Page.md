---
title: "Firefox Doesnt Load Start Page"
date: 2005-03-14
forum: Desktop Environments
---

### Post by LordCantenberry on 2005-03-14
When I start Firefox it simply doesnt load my start page.  If I click the 'HOME' button in firefox, it pops right up but will not load on start up.  I checked the settings as far as I can tell I have it set to load my.yahoo.com on startup.

Any suggestions would be helpful.

---

### Post by lorap on 2005-03-14
hi friend!
home page written in the settings says nothing, probably you need somewhere in settings mark the option like "go to the homepage at startup",look for it,it's the only possibility,don't think it be a bug.probably this option is unmarked.
have a nice day buddy!
pavel
p.s.:
i'm at institute,once i get home i'll check it if i was right.
let me know if you solve it and how.

---

### Post by RainyDay on 2005-03-14
Hi,

I too had this problem with Firefox.
After performing a clean install on a P4/512MB/60Gig system everything was ok until I ran: apt-get "update" and "upgrade".
After apt-get had finished Firefox no longer displayed the home page on boot.

I attempted to fix the problem without success but finally tried: apt-get dist-upgrade.
After apt-get completed and the machine was rebooted everything was fine, with Firefox behaving as it should.

Maybe you could try:

apt-get update
apt-get upgrade
apt-get dist-upgrade

Hope this helps...

.....RainyDay

---

### Post by LordCantenberry on 2005-03-14
Thanks for the suggestions, I ended up just reinstalling firefox and the problem resolved itself.

---

### Post by lorap on 2005-03-15
i've found an interesting thing,never really needed it,it doesn't work to me either :-)
pavel

p.s.:
i'll try to find solution out,it's interesting...

---

