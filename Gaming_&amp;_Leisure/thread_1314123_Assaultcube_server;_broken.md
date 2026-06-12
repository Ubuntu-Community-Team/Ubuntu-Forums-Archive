---
title: "Assaultcube server; broken?"
date: 2009-11-04
forum: Gaming &amp; Leisure
---

### Post by Skinnbin on 2009-11-04
I run AC GUIServer v1.0.4 r4, but for some reason it stopped working.
Everything runs normally until it sends it's request to masterserver.

Here's my output:
```
dedicated server started, waiting for clients...
Ctrl-C to exit
looking up masterserver.cubers.net...
sending request to masterserver.cubers.net...
masterserver reply: <?xml version="1.0" ?><!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"><html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"><head><title>Error 500</title
```

This is complete gibberish to me. All of the ports are forwarded and working properly as have been running it just a few days ago.

If someone could decode this message for my non-technical ears I would appreciate it. 
Thanks a bunch in advance.

---

### Post by Skinnbin on 2009-11-04
Solved. The problem was that I changed my LAN IP address.
Went onto [http://192.168.1.1/](http://192.168.1.1/) and fixed my forwarded ports from 192.168.1.100 > 192.168.1.102 for all six of my ports. 
Of course you would want to change it to whatever your inet address is.

---

