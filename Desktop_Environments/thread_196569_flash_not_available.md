---
title: "flash not available?"
date: 2006-06-14
forum: Desktop Environments
---

### Post by siman on 2006-06-14
i tried installing flash via synaptic and apt-get install flashplugin-nonfree - no errors, but it seems flash doesnt get installed. Of course I tried removing and re-installing it... nothing seems to happen. It asks me weither I'd like to download flash from the internet, I say yes and then strangly fast it starts configuring.

about:config in firefox shows me nothing about a flash-version and the ~/.moz/ff/plugin directory doesnt even exist. also in /usr/lib/mozilla/plugins and /usr/lib/mozilla-firefox/plugins there is nothing related to flash.

i noticed, that official fpdownload.macromedia.com site for downloading flash is down.. is this related?

or can someone tell me where I should look for errors?

thanks and bye
 simon

---

### Post by curiocheerio on 2007-10-09
I have had the same problem. I even went to Adobes website to download the tarball, but no luck. Regardless of what route i try to take to download the flash player from Adobe it just won't start. This has been the case for at least 3 months now. It seems really strange. Maybe i'll send adobes customer support an email about it.

The only way that i have found to get it is to find an alternate location to download it from.

---

### Post by 3rdalbum on 2007-10-10
The configuring step is where it actually downloads the Flash player from Adobe, so that's why it gets to the configuring step so quickly (there's virtually nothing in the package itself except a script).

If Adobe's FTP site is down, then this would explain why the package fails to work.

---

