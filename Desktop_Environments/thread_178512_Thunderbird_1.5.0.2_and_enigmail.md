---
title: "Thunderbird 1.5.0.2 and enigmail"
date: 2006-05-17
forum: Desktop Environments
---

### Post by cesera on 2006-05-17
I have successfully installed Thunderbird 1.5.0.2 as described in [this thread]("http://www.ubuntuforums.org/showthread.php?t=165655&highlight=thunderbird+1.5"). And everything is working fine, except for one thing:
 
When I install enigmail it doesn't work, I keep getting the following error message:
 
```
Enigmail: Enigmime service not available
 
To permanenty avoid this alert, either fix the problem or uninstall Enigmail
using the OpenPGP -> Preferences menu
```
 
I have done some research and it looks like this problem occurs when you install the wrong version of Enigmail (which I did at first), but now even with a clean install and a new ~/.thunderbird directory I still have the same problem. I downloaded the 'normal' enigmail for linux (32 bit) extension from the mozilla site. Has anyone got the same problem? Does anyone know how to fix this.

---

### Post by habicht on 2007-12-11
For the next one who has this problem, this might be the solution:
[https://bugs.launchpad.net/ubuntu/+source/enigmail/+bug/52763/comments/1](https://bugs.launchpad.net/ubuntu/+source/enigmail/+bug/52763/comments/1)

---

