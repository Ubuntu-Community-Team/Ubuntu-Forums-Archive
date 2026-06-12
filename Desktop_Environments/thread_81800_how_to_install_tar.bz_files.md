---
title: "how to install tar.bz files??"
date: 2005-10-25
forum: Desktop Environments
---

### Post by mxyzptlk on 2005-10-25
hello there i just downloaded the driver for my wlan network adapter but it comes zipped in a tar.bz file.
How can i install the files from there.

Thanks in advance

---

### Post by endersshadow on 2005-10-25
First, you need to untar it by using the following command, where foo.tar.bz2 is your file name:

```
tar -xjf foo.tar.bz2
```

If it's .gz instead of .bz2, us z instead of j in the flags.

Once that's extracted, cd into the folder that it extracted and there should be a README file that explains how to install that particular driver.

---

### Post by HermanAB on 2005-10-25
BTW, if you need some general 'How the heck do I install schtuff' help, then look at this:
[http://www.aerospacesoftware.com/compile-howto.html](http://www.aerospacesoftware.com/compile-howto.html)

Cheers,

Herman

---

