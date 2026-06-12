---
title: "Jockey fails installing restricted drivers on Dell Studio 15 (1558)"
date: 2010-07-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Aybara on 2010-07-02
I'm running 10.04 with 2.6.32-23-generic-pae, and Jockey fails with the following log:

[http://pastebin.ca/1893537](http://pastebin.ca/1893537) (never expires)

Some highlights from the end of the log:

#
2010-07-02 21:23:01,142 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
#
2010-07-02 21:23:05,549 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
#
 
#
2010-07-02 21:23:05,549 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
#
2010-07-02 21:23:05,549 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
#
2010-07-02 21:23:12,370 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
#
2010-07-02 21:23:12,449 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches

---

