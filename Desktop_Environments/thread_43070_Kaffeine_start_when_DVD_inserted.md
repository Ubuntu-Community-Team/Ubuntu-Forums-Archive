---
title: "Kaffeine start when DVD inserted"
date: 2005-06-20
forum: Desktop Environments
---

### Post by reckless2k2 on 2005-06-20
Could someone please tell me how to get Kaffeine to "autostart" when a DVD is inserted? I imagine that the same place would be where I'd edit for audio cds as well. I've looked in autostart but I can't understand anything that is in there.
Thanks in advance for any help given.

---

### Post by !nkubus on 2005-06-20
Well you need a deamon that will listen to your HAL events to do that.

The only one i know is ivman.

ivman.sf.net

then in the config file you cant uncomment the dvd insertion line , and change xine by kaffeine.

I can't tell you more, because the deamon on my computer for no apparent reason don't want to mount the dvd so kaffeine start with nothing. but  I have not investigate mor :)

I hope it gives you a small start :)

---

