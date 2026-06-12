---
title: "Wireless problems"
date: 2009-01-11
forum: General Help
---

### Post by brad_lastname on 2009-01-11
I'd previously had a dual-boot going of XP and Ubuntu and I enjoyed ubuntu so much I decided to reinstall and erase my XP partition. This went smoothly but, once everything was done, I noticed a problem. The Wireless no longer works. It reads all the networks in the area fine, but won't connect to any of them, security or not. So I hooked up a cable and tried to update. It took all night and ran at a average speed of 20 K/ps. I can use firefox and surf at excellent speeds but all synaptic programs run very, very slowly.

None of this happened previously and I'm hoping there's a simple fix to all of this.

---

### Post by mikewhatever on 2009-01-11
You obviously need to provide more info on your internet setup. What are the outputs of <ifconfig>, <sudo lshw -C network>.

---

### Post by brad_lastname on 2009-01-18
Okay, I determined the problem. I had to install the proper drivers. It was a simple fix once I figured it out. :rolleyes:

---

