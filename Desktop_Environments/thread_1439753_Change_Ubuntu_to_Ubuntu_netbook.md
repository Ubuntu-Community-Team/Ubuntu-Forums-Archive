---
title: "Change Ubuntu to Ubuntu netbook"
date: 2010-03-26
forum: Desktop Environments
---

### Post by xsoh on 2010-03-26
&#1575;&#1604;&#1587;&#1604;&#1575;&#1605; &#1593;&#1604;&#1610;&#1603;&#1605;..
Hi,

I downloaded Ubuntu on my laptop and I want to change it to 'Ubuntu netbook' because it's to slow with the Ubuntu :(

---

### Post by brunogirin on 2010-04-11
I'm not sure that changing to netbook will solve your problem because netbook is just a few packages installed on top of standard Ubuntu.

---

### Post by deconstrained on 2010-04-11
Assuming you made a separate partition for your / (root) and /home, you can always re-install Ubuntu on root without messing up your data on your /home partition. Otherwise you can back up your data by doing "rsync -av /home/ /path/to/external/harddrive/home/" which will save your everything, including settings and whatnot, and you can just re-install.
 
Ubuntu Netbook remix is a dream come true for tiny netbooks with modest hardware. Even if you can install the same packages separately, there's no guarantee that all the same configuration auto-magic will take place to install the small-screen-friendly interface and whatnot else. But even if it leaves you with a half-assed netbook remix, it's still worth a shot.

---

