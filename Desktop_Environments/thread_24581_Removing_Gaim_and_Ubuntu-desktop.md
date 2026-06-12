---
title: "Removing Gaim and Ubuntu-desktop"
date: 2005-04-07
forum: Desktop Environments
---

### Post by keyshawn on 2005-04-07
as a warty user, the latest gaim package is 1.1.2...
Over the past couple weeks, a few bugs have been patched up and 1.2.1 has been released. Aware that warty backports discontinued, I'd figure just to install it myself, src, which is fine with me.
When I attempt to remove the gaim pkg in synaptic, it requires ubuntu-desktop to be removed as well; which many packages depend on, so it can't be removed. 
Or can it ? I did a search and read that it can be safely removed with no problems, but I was just wondering - what are the eventual effects of this removal [I'm curious] :grin:


thanks,
skora.

---

### Post by HungSquirrel on 2005-04-07
The real drawback of removing ubuntu-desktop is upgrades won't go smoothly.  For example, if you remove ubuntu-desktop and upgrade from Warty to Hoary, Hoary won't know to install xorg instead of xfree86.

However, in your situation, you can probably remove gaim and ubuntu-desktop to get rid of the new gaim, then install ubuntu-desktop again to get the old one back.

---

### Post by ubuntu_demon on 2005-04-07
> **keyshawn]as a warty user, the latest gaim package is 1.1.2...
Over the past couple weeks, a few bugs have been patched up and 1.2.1 has been released. Aware that warty backports discontinued, I'd figure just to install it myself, src, which is fine with me.
When I attempt to remove the gaim pkg in synaptic, it requires ubuntu-desktop to be removed as well said:**
>  :grin:


thanks,
skora.
 you can safely remove gaim. This will break the meta-package ubuntu-desktop but this doesn't harm.

ubuntu-desktop is nice to have when you are upgrading to hoary though (to make sure everything gets upgraded).

---

### Post by keyshawn on 2005-04-07
i'll be upgrading to hoary within a few weeks, so is it a problem if I just remove ubuntu-desktop now and then later, with gaim 1.2.1 installed, redownload ubuntu-desktop ?

---

### Post by HungSquirrel on 2005-04-08
Not a problem at all.

---

