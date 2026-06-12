---
title: "gnome network administration &amp; resolv.conf"
date: 2005-06-28
forum: Desktop Environments
---

### Post by soonindallas on 2005-06-28
I hope I can express this clearly enough.

One upon a time, I misunderstood the initial setup of my network settings; I mistakenly entered a search domain in the DNS tab you see if you use the Gnome network administration tool.  I know want to get rid of it.

I tried deleting all my profiles for eth0 and eth1 and clearing it out of /etc/resolv.conf but it keeps coming back.  Even when it seems to be absent it shows up in reslov.conf then it'll come back into the network settings dialog.

What have I missed ?  what should I do to get rid of it ?

The reason I ask is that it gets appended to all my DNS requests.  The DNS then replys that it can't resolve, for ex. "www.ubuntuforms.org.myisp.com" -- of course this can't be resolved...  this slows my surfing.

is this a bug ?

thanks for your attention.

/PC

---

