---
title: "firefox &amp;epiphany crash after loading some ssl pages"
date: 2008-07-08
forum: Desktop Environments
---

### Post by luckylinux on 2008-07-08
Hi
I just upgraded my ubuntu box and now I get firefox crash when loading the adsense website.
For example, with firefox, some ssl sites load, some doesn't.
Epiphany doesn't load any ssl website at all !

If I look inside the authorities tab in firefox it's empty.
I tried to delete the cert8.db and re-created it but nothing changed.
Everytime I try to start firefox or epiphany I get this error:
```
Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.
```

Some time ago I found a thread where a user said that You had to symlink libcrypto and libssl libraries to somewhere, but I don't know more ...

AH ... in epiphany it sais "ssl disabled", but I didn't disabled it and on firefox it's enabled, thought on the adsense.google.com site it crashes.

Please help me
Thanks
Lucky Linux

---

### Post by 3321thec on 2008-07-08
Hey, first off this is my first post so bear with me....

I have seen this problem before twice, once on a Debian Etch and once on an Ubuntu (don't remember version).  To fix it on my machines I deleted the ".mozilla" directory in my user's home, apt-get --purge remove'd firefox, and then apt-get install'd firefox again.

So basically:
```

rm -rF $HOME/.mozilla
apt-get --purge remove firefox
apt-get install firefox

```

This forces Firefox to completely reconfigure, and it seemed to help.

Hope this helps!

Best Wishes,
3321thec

---

