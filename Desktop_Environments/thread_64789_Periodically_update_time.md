---
title: "Periodically update time"
date: 2005-09-12
forum: Desktop Environments
---

### Post by RadixLecti on 2005-09-12
Hi,

I've been trying to get my desktop clock (gnome) to update periodically.
I go to Time and Date settings, click the box marked "Periodically synchronize clock with Internet Servers", and get an error message:

NTP support is not running
Please run NTP support in the system to enable synchronization of your local timeserver with internet timeservers.

Then there's two buttons, "Close" and "Install NTP support".
When I hit "Install NTP support", Synaptic pops up, then "pops down" like it was never up. Disappears.

I've checked synaptic by running it normally, it works... and I have most NTP software installed: ntp, ntpdate, ntp-server, ntp.simple...

How do I enable ntp on my system?

---

### Post by heimo on 2005-09-12
Not sure. But first things I'd do is:
 ```
sudo /etc/init.d/ntpdate restart
``` 

Then I might try:
 ```
sudo apt-get --purge remove ntpdate
sudo apt-get install ntpdate
```

---

### Post by RadixLecti on 2005-09-12
Thanks, that worked. ;-)

---

