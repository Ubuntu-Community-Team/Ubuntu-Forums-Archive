---
title: "Cannot reinstall World of Goo in USC"
date: 2010-12-31
forum: Gaming &amp; Leisure
---

### Post by Quadunit404 on 2010-12-31
[FONT="Courier New"]W:Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/world-of-goo/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](https://private-ppa.launchpad.net/commercial-ppa-uploaders/world-of-goo/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  The requested URL returned error: 401[/FONT] is what the USC tells me whenever I try reinstalling World of Goo.

I bought World of Goo in the USC back before my old laptop proved itself to be a piece of junk and I had to buy a new one. I've only been able to install World of Goo once, and on the original Ubuntu installation I bought it on. Now every single time I try reinstalling it I get a 401 error. Anyone have an idea what to do?

---

### Post by Quadunit404 on 2011-01-02
*Ahem* ...Mentlegen? ([For those of you who don't get that line]("http://www.youtube.com/watch?v=LJbY4ixm_ZM"))

Well... anybody know what I should do? It's been two days since I asked this, so...

---

### Post by Arthur_D on 2011-01-02
You should probably contact Canonical and ask for advice. If it still doesn't work, maybe you can get a refund.

---

### Post by clayton2 on 2011-01-02
Yeah, maybe their server is acting funky at the moment, maybe try again a little later.

If it still doesn't work, I would either do what Arthur_D said and contact someone at Canonical (not sure who), and/or file a bug report.

---

### Post by Quadunit404 on 2011-01-03
AHA! Figured it out!

The deb line assigned to my account has the wrong username for the Token. When I realized that (found it out by looking at my other purchase) I facepalmed. Thanks, Canonical.

I'm going through the reinstallation process that will likely fail due to that and after it says [FONT="Courier New"]W:Failed to fetch blahblahblah...[/FONT] I will open up my sources.list and fix the error, then update the application cache, then reinstall it FINALLY and PROFIT! Hopefully.

[s]EDIT: nope.avi

EDIT AGAIN: I just decided to download the AMD64 .deb of WOG until I can figure out why the PPA doesn't work. I can log in using a browser with the right username and password but the PPA just spits out a Error 401 when using Ubuntu... weird.[/s] Fixed in Synaptic. This is now resolved.

---

### Post by jsgosselin on 2011-07-07
Hello,

I had the exact same problem.

I changed my Launchpad Id a while back and it caused a problem when trying to reinstall WorlofGoo because it was still using my old Launchpad ID for my private ppa URI. I replaced my new ID with the old one in the URI and everything is now working fine.

Your post helped me solved my problem and I wanted to thank you.

JS

---

