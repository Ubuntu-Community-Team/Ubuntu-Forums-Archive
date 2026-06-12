---
title: "How do I make a Samba share RW by anybody? No pswd. like xandros does."
date: 2005-10-23
forum: Desktop Environments
---

### Post by dieselpower on 2005-10-23
I have a /home/share directory that I want anybody to be able to tread and write to, without having to have a username and password. I have been trying to get it to work, but have had no luck. Xandros does an exellent job of windows networking, maybe I should install it and see exactly what they are doing. But if anyone knows how to do it here please tell me!

---

### Post by ayates on 2005-10-23
Try this:

[http://www.ubuntuguide.org/#sharepublicfoldersreadwritesecuritysh]("http://www.ubuntuguide.org/#sharepublicfoldersreadwritesecuritysh")

---

### Post by MasterPatricko on 2005-10-23
Try this for your entire smb.conf, it's much simpler and should work:

```

# Global parameters
[global]
workgroup = TUXNET
security = share

[Share]
comment = Shared files from Ubuntu
path = /home/share
read only = no
guest ok = Yes

```

NOTE: TOTALLY UNSECURE

---

### Post by dieselpower on 2005-10-24
Thank You! It worked perfectly. And no I'm not worried about security at all, I'm behind NAT and a firewall so hopefully Im OK ;)

---

### Post by HermanAB on 2005-10-25
Yup, the trick is the 'guest ok' parameter.

Here is a general Samba debug guide, which you may find useful another day, when Samba or Windows decides to show you a toffee:
[http://www.aerospacesoftware.com/samba-debug-howto.html](http://www.aerospacesoftware.com/samba-debug-howto.html)

Cheers,

H.

---

