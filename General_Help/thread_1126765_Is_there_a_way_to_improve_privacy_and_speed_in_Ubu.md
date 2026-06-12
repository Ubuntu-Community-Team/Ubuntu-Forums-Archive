---
title: "Is there a way to improve privacy and speed in Ubuntu?"
date: 2009-04-15
forum: General Help
---

### Post by wolfman1221 on 2009-04-15
Can I improve my speed and privacy in Ubuntu without removing  anything vital?

---

### Post by gfe on 2009-04-15
It depends on what your privacy and speed concerns are.

---

### Post by mb_webguy on 2009-04-15
The AdBlock Plus extension in Firefox will block ads, which will speed up web browsing.  It also blocks cookies from ad trackers which could be used to track your online activity.

[IPBlock]("http://iplist.sourceforge.net/") is similar to PeerGuardian, and blocks IP addresses known to be adservers, to monitor internet traffic, or that you'd otherwise rather not have anything to do with.

[Tor]("https://help.ubuntu.com/community/TOR") anonymizes your online activity, ensuring a high degree of privacy.  But it won't do anything to increase speed.

---

### Post by paradigm2 on 2009-04-15
> **wolfman1221 said:**
> Can I improve my speed and privacy in Ubuntu without removing  anything vital?

As mentioned your question as it is now does seem a little too open ended.  Much like asking "what is most important in life?"

Name some privacy concerns you have?

Tor, as mentioned is great at encrypting your traffic and also obscuring your ip address.  If using Firefox, the extension NoScript is great for helping to secure java, javascript, and flash.  The AdBlockPlus extension might also help a bit with privacy by blocking some ads as well as with speed by making it so that you do nto have to wait for ads to load.

For speed I would recommend the Polipo proxy.  In my tests it can increases browsing speed as it feels to you by as much as 30% or so.

If your threat model includes people possibly gaining physical access to your machine or possibly breaking in remotely, a encryption partition or folder is a great option.  I like Truecrypt for this personally.

The above are some suggestions but there are hundreds if not thousands of other angles and options.

---

