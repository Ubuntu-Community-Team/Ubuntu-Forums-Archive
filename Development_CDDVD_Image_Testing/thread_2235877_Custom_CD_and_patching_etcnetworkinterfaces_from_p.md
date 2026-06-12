---
title: "Custom CD and patching /etc/network/interfaces from package postinstall script?"
date: 2014-07-23
forum: Development CD/DVD Image Testing
---

### Post by pibara on 2014-07-23
In the past I created a custom install CD for Ubuntu 12.04 server. Recently I tried to upgrade things to 14.04, and one important thing no longer seems to work.
In my ols custom CD I had an extra self-made package that in its post-install patched the /etc/network/interfaces file so a second IP would be assigned to the
ethernet device that was already defined. Now as it turns out, while in 12.04 the file /etc/network/interfaces already existed at extra-package install time, in 14.04 as far as I could track down it only gets created during the post-install re-boot.

So basically I have this self-made deb package that during install queries the user for a second IP adress. During post-install it than wants to take for example 
the eth0 entry, create a copy of that entry using 'eth0:1' and the secondary IP address, and append that to the file that, unlike in 12.04. does not yet exist.

Are there any possibilities to fix this? What exactly happend between 12.04 and 14.04 that made that  /etc/network/interfaces is only created during post-install boot time, and is there any way to add my script to post-install boot-time execution, to a time after this file is installed?

T.I.A.

Rob

---

