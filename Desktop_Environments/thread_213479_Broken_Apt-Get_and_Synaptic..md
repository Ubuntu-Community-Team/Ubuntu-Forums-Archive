---
title: "Broken Apt-Get and Synaptic."
date: 2006-07-11
forum: Desktop Environments
---

### Post by eddorey2k3 on 2006-07-11
So I was install BOINC last night, and figured I'd do it via Synaptic (Not sure why now, much easier doing it via SH). Anyway.

So it downloads a tiny package, which then tries to download another package from alien.ssl.berkeley.edu

All is well and good, except that doesn't actually respond. Long story short, it sits there timing out, and then retrying, and so on.

If I try to run apt-get, if tells me to run ```
sudo dpkg --configure -a
``` but all this does it sit there and time out again.

Any one have any ideas of how I can make it go away, and stop trying to install? I don't even want it now, so when it does finally install I'll remove it again anyway.

The only thing, is where it says ```
(try: 5) => `/tmp/fileEV9xAd'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21.
``` 

If I just go in and delete that file/directory, will it be sorted?

Thanks

Ed.

---

