---
title: "Detecting my Wireless Card in Gnome"
date: 2006-02-20
forum: Desktop Environments
---

### Post by roostishaw on 2006-02-20
Hello,
Here goes my first post... (BTW, I am a complete linux newbie. Installed Ubuntu about 5 days ago.)

I'm having trouble getting ubuntu to detect my wireless card (D-link DWL-G520 A ). When I go into the network settings, it's only sees an the ethernet connection which I had to activate to post this. And it also sees an inactive modem connection. It was working (in the list I mean... my network uses WPA so I'm still working on that) about an hour ago. But after I did something, and I can't remember what that was... it dosn't show up it the list, so I can't activate it. But when I go into the device manager, its sees it just fine.

Any ideas how to get it back on that "list" so I can activate it? (the "list" in System>Administration>Networking) Or undo whatever I did?

Thanks!

---

### Post by roostishaw on 2006-02-20
*sigh* ... nobody knows? :neutral:

---

### Post by Pimpity Snicket on 2006-04-24
I'm having trouble w/ the same card (except I have revision b1).  Ath0 shows up but the tool doesn't work when I try configuring it.  I'm not a linux newbie but it's been quite a while since I've run any linux boxes.  I fiddled w/ iwconfig but no luck.  I may have to setup my box downstairs by my router/access point and update and hope for better luck then.

---

### Post by Jason_25 on 2006-04-24
So iwconfig and the network tool don't cause the card's settings to change?  You are confirming this with running iwconfig?  That is a very strange problem.  Normally once the interface shows up, you are 95% of the way there.

---

### Post by Pimpity Snicket on 2006-04-26
[QUOTE=Jason_25]So iwconfig and the network tool don't cause the card's settings to change?  You are confirming this with running iwconfig?  That is a very strange problem.  Normally once the interface shows up, you are 95% of the way there.[/QUOTE]

[QUOTE=CammanB]Okay... I hope/think I may be near a possible solution.... according to the list of linux-restricted-modules (madwifi) supported/tested cards, on the G520, the Rev.B doesnt work because the madwifi is too old, and it provides a link to a new build of it.  I downloaded the build and burned it to a CD... and sorry, I am new at this... what do I do with the thing... it's a .deb file, and when i double click it it opens the file extractor... I am hoping that if I can figure out how to get this thing installed it will work for my Rev. B version of the card as well since it is based on the same chipset..[/QUOTE]

It's like I'm being filibustered...  It shows up and everything and the card can be configured it just won't connect properly.

---

