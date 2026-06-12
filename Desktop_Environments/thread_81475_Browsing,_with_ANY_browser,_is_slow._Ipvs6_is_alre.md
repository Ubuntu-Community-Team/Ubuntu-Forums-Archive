---
title: "Browsing, with ANY browser, is slow. Ipvs6 is already OFF..help."
date: 2005-10-24
forum: Desktop Environments
---

### Post by Visceral Monkey on 2005-10-24
I'm running into a problem unique to Ubuntu out of all the distros I've tried so far. I've turned ipvs6 off on both the browser level and kernel level and still it persists. I'll try to hit a site, it will sit there at resolving for 5-10 seconds and then suddenly everything starts rushing in. Same thing happens when using synaptic or any other app that uses the internet. I've always tried it on two different nics, so I dont think that's the problem. I like ubuntu, but If I cant get this resolved, I'll have to switch to something else :(

Thoughts?

---

### Post by red devil on 2005-10-24
Don't know if this will help but I always enter about:config in the Firefox address bar, navigate down to Networking options and make sure the network.http.pipelining and network.http.proxy.pipelining values are set to 'true' (they're 'false' by default). This should certainly speed up Firefox, but I'm afraid I can't help you with the other speed problems.
Red Devil

---

### Post by Jeldert on 2005-10-24
I notice the same behaviour in Ubuntu. It takes a long time before a page loads in Opera and Firefox. Even when downloading software via Synaptic it takes a few (10) seconds before a download starts. But after that it goes as fast as my connection supports (250 KB/s).

When I reboot to Windows XP I don't have this problem, and in 5.04 I didn't notice this either.

---

### Post by wallijonn on 2005-10-24
You could always try the FireFox Network Tweak extension.

Are you using a HOST file?

---

### Post by leezer3 on 2005-10-24
As this is affecting both Synaptic and Firefox, this is not a Firefox problem, and no tweaks there will help things.
My suspicion is that it's almost certainly somewhere in the name resolution process. Try accessing the IP 66.102.9.104 ( [www.google.co.uk](www.google.co.uk) ). If this opens properly with no delays, then follow the instructions for setting up a static IP in this topic:
[http://ubuntuforums.org/showthread.php?t=65669](http://ubuntuforums.org/showthread.php?t=65669)
(I'm assuming you're behind a modem router, D-Link T series?)

Cheers

-Leezer-

---

### Post by Visceral Monkey on 2005-10-24
Leezer,

I love you. It is indeed a problem with my router, something I should have done basic trouble shooting on and figured out but was thrown because it worked fine under windows. A quick unplug from the router and direct plug into the modem and the problem is gone. I'll try your work around with the router tonight. Thanks to everyone for the suggestions, hopefully someone else who has this problem will get a fix from this thread as well.

Also, everyone who suggested pipelining fixes for FF. Google fastfox, it's an extension that does all those things and a few more to make things quicker.

Cheers,

Vm.

---

### Post by manicka on 2005-10-24
Try entering your settings manually into the router rather than using dhcp. My d-link router provides itself as the dns server and I have to manually enter my providers dns server address instead.

---

### Post by leezer3 on 2005-10-25
Just to let anyone know, if you have a D-Link router, most of these are affected by a 'dns proxy' bug, which is only evident using a Linux client, and means that names either fail to resolve or are slow. Setup a static IP & you should be fine.

Cheers

-Leezer-

---

### Post by wallijonn on 2005-10-25
Good fix, leezer.

I am having somewhat the same problem on a work machine, but it is probably due to only having 96MB of RAM. ;)

---

