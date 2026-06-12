---
title: "Same problem in *every* browser"
date: 2006-08-09
forum: Desktop Environments
---

### Post by deiniol on 2006-08-09
I've tried three browsers now- Epiphany, Firefox and Opera and get the same problem in all three. On certain pages the browser renders the page absurdly wide, such as in the attached screenshot.

I initially thought it was a random problem with Firefox, so I tried Epiphany. Finding the same thing, I assumed it was a bug in the Gecko engine. So I tried Opera and got the same thing. 

Interestingly, this only happens when the page is using the normal text size. If I decrease it by one level, it goes back to normal, as shown in the second screenshot. 

I'm utterly stumped and have no idea where the problem is, let alone how to fix it. Any help would be greatly appreciated.

Another problem, which is restricted to Firefox, is that I can't save or download anything. Firefox claims that it's saved the file but it never actually does. It's odd.

---

### Post by David Marrs on 2006-08-09
Is this a website you've been creating or one that you're visiting? If it's somebody else's, it's probably the case that it's only been tested against IE (a surprising number of website designers still ignore the less popular browsers). It's probably something to do with a block level element (probably div) not setting width correctly. If it's your site, check the css and make sure that your margins and width are complimenting each other correctly. Explicitly set to auto anything that should be auto. If you provide a link to the site, I could review the code for myself.

> **deiniol said:**
> Another problem, which is restricted to Firefox, is that I can't save or download anything. Firefox claims that it's saved the file but it never actually does. It's odd.
Not sure about that one, except that the url given references a proxy to the file, rather than being a direct link, and firefox is sensitive to this(?).

---

### Post by the-linux-guy on 2006-08-09
I just visited [http://community.livejournal.com/friendlyhostile/](http://community.livejournal.com/friendlyhostile/) and all looks normal to me (using firefox). You probably have something setup not right, try to create a new user onto your linux-box and try again logged in as that new user...

---

### Post by deiniol on 2006-08-09
> **David Marrs said:**
> Is this a website you've been creating or one that you're visiting?

No, it's livejournal. My css is better than that :wink:

> **the-linux-guy said:**
> I just visited [http://community.livejournal.com/friendlyhostile/](http://community.livejournal.com/friendlyhostile/) and all looks normal to me (using firefox). You probably have something setup not right, try to create a new user onto your linux-box and try again logged in as that new user...

Strangely, the other two users of this box have the same problems themselves, as does "dummyuser1" that I just created. Additionally, this seems to be a recent problem- it's only started in the last couple of weeks or so, prior to that it was fine. Any guesses as to what's not set up correctly and how I can fix it?

---

### Post by the-linux-guy on 2006-08-10
I have no idea to what could be wrong, all I know is, that website does look good, both in firefox AND in KDE's konqueror, using my pc with kubuntu 6.06 dapper drake installed... ;-) I did nothing special to my box, nor did I install anything "special", apart from a KDE theme or two...

You could examine the update history you'll find in synaptic (or see /var/log/dpkg.log if you only use apt-get) and look for recent updates that you received the last couple of weeks. Is there anything related to newly installed (updated) fonts or an entry for an updated libpango in your list ? 
If yes, try to downgrade that package to its previous version and reboot...

---

### Post by maniacmusician on 2006-08-10
well since you went to the trouble of installing Opera, there's an option (under "View" i think, but i dont have it installed here) called "Fit to Width" or something along those lines. I find it excellent for those annoyingly wide pages. I have to say, I don't get them that often, but I hope that option fixes it for you anyways

---

