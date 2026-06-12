---
title: "Install Bluebird/Greybird themes on Lucid"
date: 2011-03-24
forum: Desktop Environments
---

### Post by rent0n on 2011-03-24
Hi there,

I am looking for a clean way to install the very nice bluebird and greybird themes on Xubuntu 10.04 Lucid Lynx.

I think they require a newer engine than that installed by default on lucid.
Also where do I find the themes?

Any hint is welcome, thanks!

---

### Post by nilarimogard on 2011-03-24
You can grab Bluebird for Xubuntu from here: [https://github.com/shimmerproject/Bluebird/tarball/master](https://github.com/shimmerproject/Bluebird/tarball/master)

You'll also need the latest Murrine which you can install using the following commands:
```
sudo add-apt-repository ppa:murrine-daily/ppa
sudo apt-get update
sudo apt-get install gtk2-engines-murrine
```

---

### Post by rent0n on 2011-03-24
Thanks!
Greybird is also in the Shimmer Projects's git repo: [https://github.com/shimmerproject/Greybird](https://github.com/shimmerproject/Greybird)

Is that ppa an official murrine ppa? I can't find a link from their website: [http://www.cimitan.com/murrine/](http://www.cimitan.com/murrine/)

Is this the only way to get the required murrine engine? There's no way to get it from the official ubuntu repos or backports? I'm not sure I want daily builds, I'd prefer stable versions.

Thanks,

---

### Post by Krytarik on 2011-03-24
> **rent0n said:**
> Is that ppa an official murrine ppa? I can't find a link from their website: [http://www.cimitan.com/murrine/](http://www.cimitan.com/murrine/)

Is this the only way to get the required murrine engine? There's no way to get it from the official ubuntu repos or backports?

No, it isn't. The author apparently doesn't provide a PPA by himself.  The only way to get a more recent packaged Murrine engine is apparently  through a third party PPA.
> **rent0n said:**
> 
I'm not sure I want daily builds, I'd prefer stable versions.

In fact the versions offered by the murrine-daily PPA are not *that* daily, it offers version 0.91 currently.

Instead I recommend installing it through Elegant Gnome's PPA, it offers version 0.98 currently:
[https://launchpad.net/~elegant-gnome/+archive/ppa](https://launchpad.net/~elegant-gnome/+archive/ppa)

Greetings.

---

