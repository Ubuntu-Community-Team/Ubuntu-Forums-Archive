---
title: "Flash installed but not working"
date: 2012-12-09
forum: Desktop Environments
---

### Post by Diskdoc on 2012-12-09
I have a fairly fresh 12.04 install on a 32-bit system. "flashplugin-installer" works fine, I watch the network traffic as it downloads Flash, and after restarting Firefox I can see it among the plugins listed.

But it doesn´t work. play.spotify.com tells me to install Flash and Adobes own Flash-test-page doesn't seem to work properly.

I'll try to make due with Lightspark or Chrome but I figured someone else MUST have run into this? I saw some cryptic remarks somewhere about the Java virtual machine depending on some processor instruction that my athlonxp doesn't have. Does Flash use Java??

Anyone else with the same problem?

---

### Post by Diskdoc on 2012-12-09
I'm getting closer to this..more hints of the problem being SSE2 instruction is required by the Flash binary.

[https://bugbase.adobe.com/index.cfm?event=bug&id=3154276]("https://bugbase.adobe.com/index.cfm?event=bug&id=3154276")

[http://community.plus.net/forum/index.php?topic=105218.32]("http://community.plus.net/forum/index.php?topic=105218.32")

If this is the case, I see it as a bug that should be easily corrected in Ubuntu:

- if no SSE2 support the flashplugin-installer should throw in Lightspark instead. Better than nothing.

---

### Post by vasa1 on 2012-12-09
If your cpu is "old", recent versions of Chrome (20+) won't help either.

---

### Post by Diskdoc on 2012-12-11
Found a related bug:
[URL="https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/968759?comments=all"]
https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/968759?comments=all[/URL]

---

### Post by Diskdoc on 2012-12-11
Reported new bug: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/1088976](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/1088976)

---

