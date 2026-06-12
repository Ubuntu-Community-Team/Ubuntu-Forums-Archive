---
title: "Evolution Indicator App in 12.10"
date: 2012-11-09
forum: Desktop Environments
---

### Post by coreybell on 2012-11-09
Is there a indicator app for Ubuntu 12.10, like the one that was in 12.04?

Before I upgraded to 12.10 I had an indicator app that was in my panel with my empathy and gwibber app.

---

### Post by critin on 2012-11-09
I'm not on 12.10 at the moment and I don't use quibber at all, but did you click on the mail envelope and then on Broadcast?  Has that changed?

---

### Post by Frogs Hair on 2012-11-09
Gwibber appears under the envelope indicator in 12.10. I have no Empathy account,but there are notification options in preferences.

---

### Post by dpjg on 2012-11-10
Due to an API change there is no indicator support for evolution at the moment. See this bug report:

[https://bugs.launchpad.net/ubuntu/+source/indicator-messages/+bug/1040259](https://bugs.launchpad.net/ubuntu/+source/indicator-messages/+bug/1040259)

---

### Post by dpjg on 2012-11-10
Let me add one thing: If someone brings evolution indicator support back (to quantal) quickly, I am willing to donate 100€ (the developer might then choose to whom to give the money: herself/himself, charity, ubuntu,...)

---

### Post by dpjg on 2012-12-06
I did it myself:

Fetch current indicator code:
```
bzr branch lp:ubuntu/evolution-indicator
```Build package (install build dependencies first):
```
dpkg-buildpackage -rfakeroot -b
```Then I installed the resulting deb-package. It seems to work. Either you carry out this procedure yourself or you trust me and use the following package:

64-bit deb: [https://www.dropbox.com/s/qavc4pkbceiwddl/evolution-indicator_0.2.20-0ubuntu9_amd64.deb](https://www.dropbox.com/s/qavc4pkbceiwddl/evolution-indicator_0.2.20-0ubuntu9_amd64.deb)

---

### Post by coreybell on 2012-12-21
I have another question about evolution mail client. When ever I get ready to compose a new email, I hit new message, and it always impute two signatures in the email, and both are the same, is anyone else having this problem?

---

### Post by ibjsb4 on 2012-12-21
May be a bug

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1055497](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1055497)

---

