---
title: "Dell Bios Extremely Slow with Ubuntu"
date: 2008-01-18
forum: Dell  Ubuntu Support
---

### Post by alitanveer on 2008-01-18
I own an XPS 400 with gutsy and xp dualboot with the latest version of bios (A07). Whenever I restart the computer from ubuntu the bios loads up very slowly (about 45sec). It takes about 4 seconds to load up when I restart from windows. The same thing happens if I sutdown and then manually start the computer. I have dualboot systems on a dell laptop, the xps, and an HP laptop and this only happens with the Dells. This problem has nothing to do with the new bios as it happened with the older A05. It isn't very problematic as my computers stay on most of the time. It's just annoying to see a computer work faster with windows than with linux. I've tried tweaking the settings from the bios setup but nothing seems to work. The operating systems work extremely well and I have no problems whatsoever with any aspect of the system. Thanks

---

### Post by pbcartwright on 2008-01-18
I have an XPS laptop dual boot also. I have the same problem when I have it defaul to Linux. When I have it default to windows it comes right up. If I have it default to linux it starts the grub stage 1, then sits there for over 15 seconds before I get to the OS selection screen.. Mine is an M140 2-year old laptop.. It has been dual-boot for the entire time. Now running Kubuntu Hardy.

---

### Post by alitanveer on 2008-01-18
Other people have had problems with dell. Laptops with ubuntu preloaded have been known to malfunction extensively. Is Dell deliberately trying to make the Ubuntu experience hell for people. For all their proclaimed love for Free Software, Dell is actively making their computers uncomfortable with linux. This problem should have been fixed in the Bios a long time ago or the bios source needs to be made available so we (linux users) can fix it ourselves.:mad:

---

### Post by neptho on 2008-01-19
There is a 'quickboot' setting which tells the BIOS to not re-initialize fully, because it is a 'soft boot'.  This is likely not enabled for your case.

You can take out some RAM or just run Windows exclusively if waiting a few seconds for your many-gigs-of-RAM-to-test is too difficult to sit through.

If, instead, you are speaking of 'the blue line across the screen', you've likely installed something that requires the network to function properly, and is timing out because it's not set yet - and you have no idea what you're complaining about.

---

