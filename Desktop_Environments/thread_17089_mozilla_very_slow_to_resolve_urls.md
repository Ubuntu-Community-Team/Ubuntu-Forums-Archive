---
title: "mozilla very slow to resolve urls"
date: 2005-02-25
forum: Desktop Environments
---

### Post by tjfitz on 2005-02-25
I searched the forums and found a few other people having similar problems with firefox, which were solved by disabling ipv6.  As far as I know, I don't have ipv6 enabled on my computer.  I am on a cable modem, and connected through a router.  My resolve.conf looks just like the one on my roommate's computer (gentoo), and he isn't having a problem with web pages resolving slowly.  Any suggestions?  Perhaps ipv6 is enabled somewhere on my machine and I just don't know it....

---

### Post by Davo on 2005-02-26
Try doing this:

in the address bar type: about:config

then in filter put: network.dns.disableIPv6

and then double click it to set its value to true.

---

### Post by jdodson on 2005-02-26
next time try to run a forum search.  this is one of the most asked questions on the forum.

---

### Post by tjfitz on 2005-02-26
And I quote: > I searched the forums....   Since all the posts I found were about Firefox, and since Mozilla and Firefox (though very similar) aren't the same browser, I thought my question was appropriate.

---

