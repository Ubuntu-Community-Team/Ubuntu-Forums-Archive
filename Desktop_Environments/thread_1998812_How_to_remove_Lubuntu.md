---
title: "How to remove Lubuntu?"
date: 2012-06-07
forum: Desktop Environments
---

### Post by PDA1 on 2012-06-07
I'm running 11.04

I had installed Lubuntu and Xubuntu.

Xubuntu was removed (which messed up GnuCash too)

Now I want Lubuntu deleted also.

The only evidence I see of Lubuntu is at boot-up when there's a brief splash screen of Lubuntu

I'm trying to save diskspace, etc, etc.

How do I get rid of Lubuntu?  I don't want my system messed up like what happened above with GnuCash.  Those problems were caused by using the psychocats method....which would have also deleted LibreOffice too if I hadn't stopped it.

---

### Post by fbicknel on 2012-06-07
This is a guess... so beware.

If uninstalling the packages listed here: [https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu](https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu) and reinstalling ubuntu-desktop doesn't get it for you, may I suggest you re-install ubuntu?

Before you start anything, back up /home and keep a copy of /etc. 

Run this for a list of packages you have installed so you can pick and choose the ones you want to re-install:

```
/usr/bin/dpkg --get-selections | /usr/bin/awk '/\tinstall$/ {print $1}'| /bin/egrep -v 'linux-headers|linux-image' > /etc/applications.txt
```

---

### Post by PDA1 on 2012-06-07
Anyone else know for certain how to do it?

---

### Post by PDA1 on 2012-06-07
Fixed

Just used Synaptic to remove all traces of Lubuntu.

---

