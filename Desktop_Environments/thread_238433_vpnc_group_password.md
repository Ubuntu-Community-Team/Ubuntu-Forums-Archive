---
title: "vpnc group password"
date: 2006-08-17
forum: Desktop Environments
---

### Post by RoyCowboy on 2006-08-17
I have a bit of a problem setting up my vpn connection. I don't have the group password and I dont have access to it because of security reasons.
What I do have is the password encrypted as md5. Is there a way to tell vpnc to use this md5-string instead of me having to type in the password when I connect? A config file or something similar for example..?

This might sound a bit suspicious :) but but I've only been given a pcf-file containing the information I need. This file is ofcourse for a windows cisco client.

Thanks in advance

---

### Post by RoyCowboy on 2006-08-17
Nevermind. I managed to load the pcf file with the nm-applet plugin..

---

### Post by gkiller on 2006-09-15
This is an older thread but I thought I'd answer, because somebody might have the same problem.

I was in the same situation, and found out that you can use your encrypted group password with vpnc directly. Just put the following line into your .conf file:
```
IPSec obfuscated secret <hex string>
```
For more options, type in terminal:```
vpnc --long-help
```
Or you can decrypt the group password here:
[http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

---

