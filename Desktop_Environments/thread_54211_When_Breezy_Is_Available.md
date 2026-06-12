---
title: "When Breezy Is Available"
date: 2005-08-03
forum: Desktop Environments
---

### Post by retsel on 2005-08-03
I understand a new version of Kubuntu (Breezy) will be out in Oct. I wasn't involved when Hoary came out, so I haven't been through the upgrade procedure. How do I upgrade to the new version without losing all of the settings and changes that I've made since installing Hoary? If there's something already published on this I haven't been able to find it.

---

### Post by TravisNewman on 2005-08-03
basically you'd just edit your /etc/apt/sources.list file and change all instances of the word "hoary" to "breezy"

Then "sudo apt-get update" and "sudo apt-get dist-upgrade"

It may not be that easy, but problems that arise are usually easy to overcome.

---

### Post by rosslaird on 2005-08-04
Yes, not that easy at all, if you look at the breezy sub-forum. Lots of trouble still with breezy, apparently. A few intrepid souls have migrated across, but many people are having serious issues. There are a few posts in the breezy sub-forum that give a kind of status about how things look at any given moment (the "how broken are we" thread is good, as are a few others on the main page of the sub-forum).
I'm going to wait another month or so before jumping to breezy.

Ross

---

