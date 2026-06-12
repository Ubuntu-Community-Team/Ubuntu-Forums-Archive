---
title: "Starting oddity"
date: 2005-12-28
forum: Desktop Environments
---

### Post by Sef on 2005-12-28
I have just installed 5.10, Breezy, on my friend's laptop: Compaq Pressario 1200.  There is one oddity when it that I wonder if it indicates a problem or not.  As Ubuntu is initializing, the programs are scolling up just fine, when it stops at 'Synchronizing  o clock to ntp.ubuntulinux.org'.   After 5-10 seconds, the scroll bar disappear s, and the  programs are highlighted in white with an ok at the end.  After another 5-10 seconds, it starts scrolling again on that page and then finishes booting just fine.

Any ideas of what is needed to be done to fix this bug?

---

### Post by HermanAB on 2005-12-28
Not a problem.

For the network time protocol to work, the network has to work.  It takes a little while for connectivity to be established, which is why you see a delay.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by dcstar on 2005-12-28
[QUOTE=Sef]I have just installed 5.10, Breezy, on my friend's laptop: Compaq Pressario 1200.  There is one oddity when it that I wonder if it indicates a problem or not.  As Ubuntu is initializing, the programs are scolling up just fine, when it stops at 'Synchronizing  o clock to ntp.ubuntulinux.org'.   After 5-10 seconds, the scroll bar disappear s, and the  programs are highlighted in white with an ok at the end.  After another 5-10 seconds, it starts scrolling again on that page and then finishes booting just fine.

Any ideas of what is needed to be done to fix this bug?[/QUOTE]
It is trying to make contact with that site over the Internet, if the connection is not yet up (or is not there, like on a laptop without a network connection), it will stall at that point.

You edit /etc/default/ntpdate to use another timeserver, or comment out all the entries for it not to run.

---

