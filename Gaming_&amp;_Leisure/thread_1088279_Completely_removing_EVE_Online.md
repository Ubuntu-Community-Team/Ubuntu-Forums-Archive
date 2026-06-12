---
title: "Completely removing EVE Online"
date: 2009-03-05
forum: Gaming &amp; Leisure
---

### Post by Paulzy on 2009-03-05
I went to EVE site and followed thiuer directions: [here]("http://support.eve-online.com/Pages/KB/Article.aspx?id=391"). However, THAT doesn not remove the menu items or anything else. Because I cannot locate the Starter Kit they are talking about in either my package mangers for Ubuntu Linux 8.10. Can you give me more explicit details on to completely remove EVEO from my Linux system?

The Menu items are still there and the /usr/bin/eve, /etc/eve, usr/share/doc/eve, & usr/lib/eve files & folders are still there as well.

Running the GDEBI package manager just asks to re-install, but offers no option to uninstall, neither does the EVE Configuration tool.

Please help thanks.
Ubuntu Hardy 8.04.2
Linux 2.6.24-23.48
:(
Paul

---

### Post by Vadi on 2009-03-06
Try going to System &#9656; Adminsitration &#9656; Synatic and remove it from there.

---

### Post by Firestem4 on 2009-03-07
I believe```
sudo apt-get remove eve-online
``` Will work. If not maybe a variant? I installed EVE-Online client but I removed it myself when I realized my computer wasn't powerful enuogh to run the client. 

You will have to delete the .cedega folder too to get rid of about 1.5 gigs worth of data.

---

### Post by Firestem4 on 2009-03-07
Oh, one more note. If it isn't one of those It might be under some variant of TotalGaming (ttg). I hoenstly forgot and I'm sorry. maybe you can find out what the command string is to launch EVE and use that as the name?

---

### Post by Paulzy on 2009-03-09
Thanks guys. I did try to Synaptic, but I can't recall HOW I missed that. I think when I entered "eve" and saw all the choices with "eve" I gave up. But I found it and removed it.

I love this community...:popcorn:
---
I actually liked playing the game and was surprised I could play it on Ubuntu. All the graphics options were cranked up to maximum, he heh..but even though it reminded me of *Earth: Space and Beyond* (remember that?), it just wasn't spacey enough - for one you can't leave your ship and the whole thing seems to focused on selling and trading and no real game play or story.

---

### Post by Bölvaður on 2009-03-09
> **Firestem4 said:**
> I believe```
sudo apt-get remove eve-online
``` Will work. If not maybe a variant?

nah I think it is only "eve" not "eve-online".

---

