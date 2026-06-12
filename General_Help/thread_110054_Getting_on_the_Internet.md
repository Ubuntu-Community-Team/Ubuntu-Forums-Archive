---
title: "Getting on the Internet"
date: 2005-12-29
forum: General Help
---

### Post by Shalaw on 2005-12-29
I've just ask my local phone/internet provider to help me set my laptop running Ubuntu up to the internet.  Their reply was that they didn't support it.  How can they not?  If I can dial in for dial up can't I operate Ubuntu?

---

### Post by wanger123 on 2005-12-30
Hi Shalaw, just open up a terminal and type: sudo pppconfig 
and follow the instructions from here: [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) and then download bbppp from the repositories. If you are on dialup, hopefully you have a conexant or lucent chipped modem which will work. What brand of laptop do you have? I am running a dell 9300 with the linuxant driver with no probs.
I am happy to discuss the setup with you, as you may need to edit some of the /etc/ppp files

[EDIT] I can assist with Dialup or ethernet/LAN as I use both
cheers
wanger

---

